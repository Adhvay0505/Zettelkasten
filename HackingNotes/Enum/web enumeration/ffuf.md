- minimal ffuf one-liner
```
ffuf -u http://10.10.10.123/FUZZ -w ~/wordlists/common.txt -t 40 -mc 200
```

- Basic fuzz (directory) — results printed to terminal
```
ffuf -u http://10.10.10.123/FUZZ -w ~/wordlists/common.txt -t 50 -mc 200,301,302
```

- Fuzz with extensions
```
ffuf -u http://10.10.10.123/FUZZ -w ~/wordlists/common.txt -e .php,.html,.bak -t 50 -mc 200
```

- Parameter fuzzing (query param)
```
ffuf -u "http://10.10.10.123/search?q=FUZZ" -w ~/wordlists/params.txt -t 40 -mc 200
```

- Recursion (careful — may generate lots of requests)
```
ffuf -u http://10.10.10.123/FUZZ -w ~/wordlists/common.txt -recursion -recursion-depth 2 -t 40 -mc 200
```

- Use custom headers / cookies (auth testing)
```
ffuf -u http://10.10.10.123/FUZZ -w ~/wordlists/common.txt -H "User-Agent: Mozilla/5.0" -H "Authorization: Bearer TOKEN" -b "session=abcd" -t 40 -mc 200
```

- Filter out noisy responses by status code and/or response size
```
ffuf -u http://10.10.10.123/FUZZ -w ~/wordlists/common.txt -t 50 -fc 404 -fs 3456 -mc 200
```

- Follow redirects
```
ffuf -u http://10.10.10.123/FUZZ -w ~/wordlists/common.txt -r -t 50 -mc 200
```
