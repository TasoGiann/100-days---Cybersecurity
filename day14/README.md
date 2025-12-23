# 🛡️ Day 14: Active Defense (Fail2Ban)

## 📝 Executive Summary
Static firewalls are essential, but they cannot distinguish between a legitimate user failing a password once and a botnet trying thousands of times. Today, I deployed **Fail2Ban** to create an "Active Defense" layer. This tool monitors logs for suspicious behavior and dynamically updates firewall rules to block attackers in real-time.

## 💻 Configuration Steps

### 1. The Strategy
I installed Fail2Ban and configured a "Jail" for the SSH service.
* **Trigger:** 3 failed login attempts within a specific time window.
* **Action:** Ban the source IP address for 10 minutes.
* **Customization:** I ensured Fail2Ban was monitoring Port 2222 (my hardened SSH port) rather than the default Port 22.

![Fail2Ban Config](./fail2ban_config.png)

### 2. Testing the Defense
I simulated a brute-force attempt from my Kali machine. After the 3rd failed password entry, Fail2Ban detected the pattern and instructed the firewall to drop all traffic from the attacker's IP.

**Verification Command:**
```bash
sudo fail2ban-client status sshd
Evidence: The status report below confirms that the attacker's IP (192.168.160.130) has been placed in the "Currently banned" list.
