Markdown

# 🔐 Day 4: Initial Access & Post-Exploitation

## 📝 Executive Summary
After confirming the SSH service was active, I utilized valid credentials (simulating a compromised account) to gain shell access. Once inside, I performed **Post-Exploitation Enumeration** to understand the environment.

## 💻 Commands & Analysis

### 1. Accessing the Target
```bash
ssh ubuntu@192.168.160.x
Credentials: ubuntu / password (Lab Configuration)

Status: Access Granted

2. Local Enumeration
Once logged in, I ran the following commands to establish situational awareness:

whoami: Confirmed I am running as the ubuntu user (low privilege).

uname -a: Verified the Kernel version (6.8.0-88-generic). This is useful for checking Kernel exploits.

ss -tulnp: Checked for internal listening ports.

Observation: No hidden internal services (like MySQL on 3306) were found listening locally.

ip a: Confirmed the network interface matches the target IP.

