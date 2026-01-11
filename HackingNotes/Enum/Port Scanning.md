
- using `rustscan` (run first as its faster, you will get a general feel of what ports are open, for more complex scans and to find the services running, run nmap)

```
rustscan -a 10.10.10.123
```

- using `nmap`

```
nmap -sC -sV 10.10.10.123
```

- nmap fast top ports

```
nmap -sS -Pn --top-ports 100 10.10.10.123
```

- list open ports, service versions for popular ports in CTF scenarios

```
nmap -sV -sC -p22,80,443,139,445 10.10.10.123
```

- nmap quick service/version detection (+ scripts)

```
nmap -sV -sC -Pn -p- -T4 10.10.10.123
```


