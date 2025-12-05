# 🔐 Day 4: Initial Access & Post-Exploitation

## 📝 Executive Summary
After confirming the SSH service was active, I utilized valid credentials (simulating a compromised account) to gain shell access. Once inside, I performed **Post-Exploitation Enumeration** to understand the environment.

## 💻 Commands & Analysis

### 1. Accessing the Target
```bash
ssh ubuntu@192.168.160.x
Credentials: ubuntu / password (Lab Configuration)

2. Local Enumeration
Once logged in, I ran the following to map the system:

whoami: Confirmed I am the 'ubuntu' user.

uname -a: Checks Kernel version.

ss -tulnp: Checks for other internal listening ports.

ip a: Confirms network interfaces.
