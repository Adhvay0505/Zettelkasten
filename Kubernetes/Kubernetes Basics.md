## ✅ Why Kubernetes

- Kubernetes manages containers at scale  
  - Many containers?  
  - Across servers?  
  - Scaling? updates? failures? -> it is complex to handle all of this manually  
- Solution: Kubernetes (K8's) = Container Orchestrator  
- Benefits: Automation, Scalability, High Availability (HA) etc

---

## ⚙️ Setup Kubernetes

- Tool: `kubectl` (kube - control) - command line for K8's
- Verify setup:

```bash
$ kubectl get nodes
NAME           STATUS   ROLES           AGE   VERSION
k8s-master     Ready    control-plane   10m   v1.29.0
```

- (Expect 1 node, status: Ready)

---

## 📦 Pod

- A pod is the smallest unit of deployment in kubernetes  
- A pod is a collection of containers(multiple containers) & a few other things in which you can run your application  
- Usually its just 1 container when you start out  
- Ephemeral (They can die/be replaced)

```bash
$ kubectl run nginx --image=nginx
pod/nginx created
```

this created 1 pod of nginx

```bash
$ kubectl get pods 
NAME      READY   STATUS    RESTARTS   AGE
nginx     1/1     Running   0          5s
```

This is a standalone unit of nginx, the smallest unit you can get, a pod.

```bash
$ kubectl delete pod nginx
pod "nginx" deleted
```

---

## 📌 Deployment

- A "deployment" is a collection of pods  
- It manages pods  
- Declares "Desired State" (e.g 3 replicas of nginx image)  
- Ensures current state == Desired State, It makes sure they are the same(Handles Failures)

```bash
$ kubectl create deployment my-nginx --image=nginx
deployment.apps/my-nginx created
```

```bash
$ kubectl get pods
NAME                READY   STATUS    RESTARTS   AGE
my-nginx-8328f82j4  1/1     Running   0          5s
```

```bash
$ kubectl get deployment.apps
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
my-nginx   1/1     1            1           10s
```

- what if i want multiple instances? instead of just one 

```
$ kubectl delete deployments.apps my-nginx 
deployment.apps "my-nginx" is deleted

$ kubectl get pods
No resources found in default namespace
```

```bash
$ kubectl create deployment my-nginx --image=nginx --replicas=3
deployment.apps/my-nginx created
```

```bash
$ kubectl get pods
NAME                READY   STATUS    RESTARTS   AGE
my-nginx-8328f82j4  1/1     Running   0          5s
my-nginx-8328f83j5  1/1     Running   0          5s
my-nginx-8328f84j6  1/1     Running   0          5s
```

lets delete one of these to see what happens

```bash
$ kubectl delete pod my-nginx-8328f82j4
pod "my-nginx-8328f82j4" deleted
```

this only deletes my-nginx-8328f82j4

```bash
$ kubectl get pods
NAME                READY   STATUS    RESTARTS   AGE
my-nginx-5765f9534  1/1     Running   0          2s
my-nginx-8328f83j5  1/1     Running   0          20s
my-nginx-8328f84j6  1/1     Running   0          20s
```

however, the deployment makes sure 3 replicas remain, by creating another one to replace the pod we killed. This ensures that the `current state = desired state`

---
### 🖧 Networking

- All pods each get their own IP Addresses

```bash
$ kubectl get pods -o wide

NAME                READY   STATUS    RESTARTS   AGE   IP            NODE 
my-nginx-5765f9534  1/1     Running   0          2s    10.244.1.23   worker-node2
my-nginx-8328f83j5  1/1     Running   0          20s   10.244.2.45   worker-node1
my-nginx-8328f84j6  1/1     Running   0          20s   10.244.2.46   worker-node1
```

- If i delete one pod

```bash
$ $ kubectl delete pod my-nginx-8328f83j5
pod "my-nginx-8328f83j5" deleted
```

- The deleted pod is recreated and gets a new IP address everytime

```bash
$ kubectl get pods -o wide

NAME                READY   STATUS    RESTARTS   AGE   IP            NODE 
my-nginx-5765f9534  1/1     Running   0          12s   10.244.1.23   worker-node2
my-nginx-8d9f84c76  1/1     Running   0          2s    10.244.3.12   worker-node1
my-nginx-8328f84j6  1/1     Running   0          30s   10.244.2.46   worker-node1
```

- we can solve this problem by using services
---
### ☢️ Services

- Expose a deployment as a service 

```bash
$ kubectl expose deployment my-nginx --port=80
services/my-nginx exposed
```

```bash
$ kubectl get service my-nginx

NAME        TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)   AGE
my-nginx    ClusterIP   10.96.123.29   <none>        80/TCP    5s
```

- This IP address is a ClusterIP, and it is going to be stable

```bash
$ kubectl port-forward svc/my-nginx 8080:80
Forwarding from 127.0.0.1:8080 -> 80
Forwarding from [::1]:8080 -> 80
```

- Forwards your local port **8080** to the service's port **80** inside the cluster.
- You can now access the service locally at: http://localhost:8080

---
### ⚖️ Scaling

```shell
$ kubectl get pods
NAME                        READY   STATUS    RESTARTS   AGE
my-nginx-7c758b5b8d-2kq4z   1/1     Running   0          5m
my-nginx-7c758b5b8d-9plmx   1/1     Running   0          5m
my-nginx-7c758b5b8d-xr5ft   1/1     Running   0          5m
```

- I will now scale this deployment to have 10 replicas running

```shell
$ kubectl scale deployment my-nginx --replicas=10
deployment.apps/my-nginx scaled
```

```bash
$ kubectl get pods
NAME                        READY   STATUS    RESTARTS   AGE
my-nginx-7c758b5b8d-2kq4z   1/1     Running   0          10m
my-nginx-7c758b5b8d-9plmx   1/1     Running   0          10m
my-nginx-7c758b5b8d-xr5ft   1/1     Running   0          10m
my-nginx-7c758b5b8d-a1b2c   1/1     Running   0          1m
my-nginx-7c758b5b8d-b3d4e   1/1     Running   0          1m
my-nginx-7c758b5b8d-c5f6g   1/1     Running   0          1m
my-nginx-7c758b5b8d-d7h8i   1/1     Running   0          1m
my-nginx-7c758b5b8d-e9j0k   1/1     Running   0          1m
my-nginx-7c758b5b8d-f1l2m   1/1     Running   0          1m
my-nginx-7c758b5b8d-g3n4o   1/1     Running   0          1m
```

```shell
$ kubectl get deployments.apps
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
my-nginx   10/10   10           10          15m
```

---

### 🧹 Cleaning / Deleting

- Lets check the services 

```shell
$ kubectl get svc
NAME         TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)    AGE
kubernetes   ClusterIP   10.96.0.1      <none>        443/TCP    1d
my-nginx     ClusterIP   10.96.123.29   <none>        80/TCP     20m
```

- To delete a Kubernetes service

```shell
$ kubectl delete svc my-nginx
service "my-nginx" deleted
```

- Lets check the deployments 

```shell
$ kubectl get deployments.apps
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
my-nginx   10/10   10           10          15m
```

- It would'nt work if i start deleting pods now because then the deployment would just keep recreating them.
- If i want to get rid of the pods i would have to delete the deployment. 

```shell
$ kubectl delete deployment my-nginx
deployment.apps "my-nginx" deleted
```

- If i run 

```shell
$ kubectl get pods
No resources found in default namespace.
```

- Everything is cleaned up and I have nothing running in my cluster anymore

I made these notes by following this video
https://youtu.be/9AKSLbfen6w?si=71OoA7Rl2ODs7jBE
Watch this one for Kubernetes Networking
https://youtu.be/J8jAzqbXxjE?si=_3ZMPfCKT-oPqLcf

