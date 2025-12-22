# 🛡️ Day 13: Host-Based Firewall (UFW)

## 📝 Executive Summary
Following the hardening of the SSH service, I implemented a network layer defense using UFW (Uncomplicated Firewall). I applied a "Default Deny" policy, which ensures that any traffic not explicitly authorized is silently dropped.

## 💻 Configuration Steps

### 1. Defining the Rules
I configured UFW to block all incoming connections by default. I then created a specific exception for TCP Port 2222 to maintain SSH access.

**Commands:**
```bash
sudo ufw default deny incoming
sudo ufw allow 2222/tcp
sudo ufw enable
