
- minimal gobuster one-liner
```
gobuster dir -u http://10.10.10.123/ -w ~/wordlists/common.txt
```

- Basic directory scan
```
gobuster dir -u http://10.10.10.123/ -w ~/wordlists/common.txt -t 50 -x php,html,txt -s "200,204,301,302,307,401"
```

- Hide noisy status codes (e.g. 403 and 404)
```
gobuster dir -u http://10.10.10.123/ -w ~/wordlists/common.txt -t 50 -b 403,404
```

- Ignore TLS cert errors for HTTPS
```
gobuster dir -u https://10.10.10.123/ -w ~/wordlists/common.txt -t 40 -k
```

- Virtual-host discovery (vhosts)
```
gobuster vhost -u http://10.10.10.123 -w ~/wordlists/vhosts.txt -t 80
```

- With custom extensions
```
gobuster dir -u http://10.10.10.123/ -w ~/wordlists/common.txt -t 50 -x php,html,bak,zip
```

use this in combination with [[ffuf]], ffuf is faster 