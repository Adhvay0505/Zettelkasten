in the case of ruby, sometimes you may end up in an IRB (Interactive Ruby)
```
irb(main):001:0>
```

In your IRB prompt, run:
```bash
exec "/bin/bash"
```

- `exec` replaces the current Ruby process with a bash shell.
- If successful, this gives you **a fully interactive shell** — like being in a real terminal.
