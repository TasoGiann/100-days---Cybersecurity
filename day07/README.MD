# Day 7: Linux Privilege Escalation (Sudo Rights)

## Executive Summary
Getting a foothold is only the beginning. To fully compromise a machine, one must escalate privileges to `root`. Today, I explored **Sudo Misconfigurations**, specifically abusing "NOPASSWD" entries which allow a standard user to run commands with administrative privileges.

## 💻 Technical Analysis

### 1. Enumeration (`sudo -l`)
The first step in Linux Post-Exploitation is checking the current user's permissions.
Command: `sudo -l`

* **Finding:** The user `ubuntu` is allowed to run `/usr/bin/python3` as root without a password.
* **Risk:** Python has a module (`os`) that allows interaction with the operating system. If we can run Python as root, we can tell the OS to give us a shell.

### 2. The Exploit (GTFOBins)
Using the methodology from **GTFOBins**, I constructed a one-line payload to spawn a system shell (`/bin/sh`) via Python.

**Payload:**
```bash
sudo python3 -c 'import os; os.system("/bin/sh")'
3. Impact (Root Access)
The payload successfully executed, elevating my session from ubuntu (uid=1000) to root (uid=0). I now have full control over the operating system.
