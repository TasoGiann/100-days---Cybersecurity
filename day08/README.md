# 🛡️ Day 8: Privilege Escalation (SUID Binaries)

## 📝 Executive Summary
Privilege escalation often relies on finding files with "Set User ID" (SUID) permissions. If a binary is owned by root and has the SUID bit set, it executes with root privileges regardless of who runs it. Today, I hunted for misconfigured SUID binaries to gain system control.

## 💻 Technical Analysis

### 1. Enumeration (Finding SUID Files)
I used the `find` command to scan the entire filesystem for binaries with the SUID bit (permission 4000) active.

```bash
find / -perm -4000 2>/dev/null
Finding: /usr/bin/find appeared in the list. This is abnormal for a standard Linux installation.

Risk: The find utility has an -exec flag, which allows it to execute other commands. Since find itself runs as root (due to SUID), any command it executes will also run as root.

2. The Exploit
I utilized the GTFOBins methodology to exploit the binary. I instructed find to execute /bin/sh.

Bash

/usr/bin/find . -exec /bin/sh -p \; -quit
3. Impact (Root Access)
The command spawned a new shell session. Verifying with whoami confirmed that I had successfully escalated privileges to root.
