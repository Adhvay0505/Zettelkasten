# Kubernetes Learning Notes (Phase 1-4)

> Created during minikube practice session, entire cluster running inside a Debian 12 VM

---

## Phase 1: Starting the Cluster

### What is minikube?
- It's a **single-node Kubernetes cluster** running inside a VM (or container)
- Think of it as a "mini data center" on your computer

### What did `minikube start` do?
- Created a virtual machine (or container)
- Installed Kubernetes components on it (kubelet, kube-proxy, etc.)
- This VM becomes your **node** - the worker that runs your apps
- Always remember to alias `minikube kubectl --` to `kubectl `

```bash
alias kubectl="minikube kubectl --"
```

### Commands
```bash
# Start minikube
minikube start --driver=docker   # or --driver=virtualbox

# Verify it's running
kubectl cluster-info
kubectl get nodes
```

### Expected Output
```
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   1m    v1.28.0
```

Your node is **Ready** - meaning it's healthy and can accept workloads.

---

## Phase 2: Pods

### What is a Pod?
- The **smallest deployable unit** in Kubernetes
- It's a wrapper around one or more containers
- In 99% of cases, a pod = 1 container

### Commands
```bash
# Create a pod running nginx
kubectl run nginx --image=nginx

# See it running
kubectl get pods

# See details (shows IP, node, events)
kubectl describe pod nginx

# View logs
kubectl logs nginx

# Execute into pod (SSH)
kubectl exec -it nginx -- /bin/bash

# Delete pod
kubectl delete pod nginx
```

### Diagram
```
┌─────────────────────────────────────────┐
│  Node (minikube)                        │
│  ┌─────────────────────────────────┐   │
│  │  Pod: nginx                     │   │
│  │  ┌───────────────────────────┐  │   │
│  │  │ Container: nginx          │  │   │
│  │  │ (port 80)                 │  │   │
│  │  └───────────────────────────┘  │   │
│  └─────────────────────────────────┘   │
└─────────────────────────────────────────┘
```

### Important
- Pods are **ephemeral** - if you delete it, it's gone forever (no auto-recovery)

---

## Phase 3: Deployments

### Why do we need Deployments?
- Pods alone don't self-heal or scale
- Deployments = **manages Pods** for you

### What does a Deployment give you?

| Feature | How it works |
|---------|--------------|
| **Self-healing** | If a pod crashes, Deployment automatically creates a new one |
| **Scaling** | `kubectl scale` adds/removes pod replicas |
| **Rolling updates** | Update image version, Kubernetes updates pods one-by-one |
| **Rollback** | Go back to previous version if something breaks |

### Commands
```bash
# Create a deployment (better than raw pods)
kubectl create deployment myapp --image=nginx

# See the deployment
kubectl get deployments

# Scale it up
kubectl scale deployment myapp --replicas=3

# See pods now running
kubectl get pods

# Delete a pod - watch K8s recreate it automatically!
kubectl delete pod <pod-name>
```

### Diagram
```
┌────────────────────────────────────────────────────────┐
│  Deployment: myapp                                    │
│  ┌────────────────────────────────────────────────┐   │
│  │  ReplicaSet: myapp-xxxxx                      │   │
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐         │   │
│  │  │  Pod 1  │ │  Pod 2  │ │  Pod 3  │         │   │
│  │  │ nginx   │ │ nginx   │ │ nginx   │         │   │
│  │  └─────────┘ └─────────┘ └─────────┘         │   │
│  └────────────────────────────────────────────────┘   │
└────────────────────────────────────────────────────────┘
```

---

## Phase 4: Services

### What's the problem?
- Pods have random IPs (e.g., 10.244.1.5)
- Pods die and get new IPs
- You need a **stable endpoint** to access your app

### What is a Service?
- A **stable IP and DNS name** that routes to your pods
- Load balances traffic across all pod replicas

### Service Types

| Type | What it does |
|------|--------------|
| **ClusterIP** | Internal only - other pods can reach it. Default. |
| **NodePort** | Exposes on each node's IP at a specific port (30000-32767) |
| **LoadBalancer** | External cloud load balancer (not useful in minikube) |
| **ExternalName** | DNS alias |

### Commands
```bash
# Expose your deployment inside the cluster
kubectl expose deployment myapp --port=80

# See the service
kubectl get svc

# Access it (from within cluster)
kubectl run test --rm -it --image=busybox --restart=Never -- wget -O- myapp

# Or expose externally via NodePort
kubectl expose deployment myapp --port=80 --type=NodePort

# Opens in browser
minikube service myapp
```

### Diagram
```
┌─────────────────────────────────────────────────────────┐
│  Service: myapp (ClusterIP: 10.100.100.100)            │
│         │                                              │
│    ┌────┴────┬────────────────┐                         │
│    ▼         ▼                ▼                        │
│ ┌──────┐ ┌──────┐      ┌──────┐                        │
│ │ Pod 1│ │ Pod 2│      │ Pod 3│                        │
│ └──────┘ └──────┘      └──────┘                        │
└─────────────────────────────────────────────────────────┘
```

---

## Summary: How It All Fits Together

```
┌──────────────────────────────────────────────────────┐
│                    CLUSTER                           │
│                                                      │
│  ┌──────────────────────────────────────────────┐   │
│  │  Node (minikube)                             │   │
│  │                                              │   │
│  │  ┌────────────────────────────────────────┐  │   │
│  │  │  Service (stable IP, load balancer)   │  │   │
│  │  │         ▲                              │  │   │
│  │  │         │                              │  │   │
│  │  │  ┌──────┴──────┐                      │  │   │
│  │  │  │ Deployment  │ (manages replicas)  │  │   │
│  │  │  └──────┬──────┘                      │  │   │
│  │  │         │                              │  │   │
│  │  │    ┌────┴────┐                         │  │   │
│  │  │    ▼         ▼                         │  │   │
│  │  │  ┌─────┐  ┌─────┐   (Pods)             │  │   │
│  │  │  │ Pod │  │ Pod │                     │  │   │
│  │  │  └─────┘  └─────┘                     │  │   │
│  │  └────────────────────────────────────────┘  │   │
│  └──────────────────────────────────────────────┘   │
└──────────────────────────────────────────────────────┘
```

---

## Quick Reference: Common Commands

```bash
# Cluster
kubectl cluster-info
kubectl get nodes

# Pods
kubectl get pods
kubectl describe pod <name>
kubectl logs <name>
kubectl exec -it <name> -- /bin/bash
kubectl delete pod <name>

# Deployments
kubectl get deployments
kubectl create deployment <name> --image=<image>
kubectl scale deployment <name> --replicas=3
kubectl delete deployment <name>

# Services
kubectl get svc
kubectl expose deployment <name> --port=<port>
kubectl delete svc <name>

# General
kubectl get all          # Get all resources
kubectl -n <namespace>   # Specify namespace
kubectl --help           # Get help
```

Definitely the best documentation tutorial I've seen until now :-
https://minikube.sigs.k8s.io/docs/tutorials/kubernetes_101/

