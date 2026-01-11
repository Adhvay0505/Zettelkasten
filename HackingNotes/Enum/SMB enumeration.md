
- enum4linux quick

```
enum4linux -a 10.10.10.123 > enum4linux.txt
```

- list shares (smbclient)

```
smbclient -L //10.10.10.123 -N        # -N = no password
```

- check share contents

```
smbclient //10.10.10.123/sharename -N -c 'ls; get secret.txt'
```

- smbmap (list shares & perms)

```
smbmap -H 10.10.10.123
```
