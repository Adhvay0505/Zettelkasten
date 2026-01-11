Stabilize a dumb shell:

Go-to command after catching a dumb shell is to use Python to spawn a pty.
The pty module let’s you spawn a psuedo-terminal that can fool commands like `su`
into thinking they are being executed in a proper terminal.
To upgrade a dumb shell, simply run the following command:

```bash
python -c 'import pty; pty.spawn("/bin/bash")'
```

sometimes, ``python`` alone wont work, you may need to specify ``python3``.

```bash
python3 -c 'import pty; pty.spawn("/bin/bash")'
export TERM=xterm
stty raw -echo; fg
stty rows 24 columns 80
```

- if Python has setuid capability or is run as root in cron. [[Privelege Escalation### Spawn a Root Shell via Python (If Writable)]]

- For getting a full bash environment in an already working interactive shell where you are root, check [[Ruby Interactive Shell]] & [[Nmap Interactive Shell]]

