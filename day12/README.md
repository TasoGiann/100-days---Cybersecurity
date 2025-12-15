# 🛡️ Day 12: SSH Hardening (Blue Team)

## 📝 Executive Summary
After analyzing the logs of my brute-force attack, I implemented hardening measures to secure the SSH service. By changing default configurations, I significantly reduced the attack surface, making the "spray and pray" attacks I performed earlier ineffective.

## 💻 Hardening Steps

### 1. Configuration Changes
I modified the `/etc/ssh/sshd_config` file to deviate from standard insecure defaults.

* **Port 22 → 2222:** Changing the default port stops basic automated scanners and botnets that only look at port 22.
* **PermitRootLogin → no:** This prevents an attacker from brute-forcing the `root` account directly. They must now crack a standard user's password first and *then* find a privilege escalation vulnerability, doubling the effort required.

### 2. Verification
I attempted to connect from my attacker machine using the standard command. The connection was refused, confirming the service is no longer listening on the default port.

