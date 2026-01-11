# 🛡️ Day 15: Automated Security Auditing (Lynis)

## 📝 Executive Summary
After spending four days implementing specific defenses (SSH, UFW, Fail2Ban), I needed a way to validate the overall security posture of the system. I utilized **Lynis**, an industry-standard security auditing tool, to perform a comprehensive scan of the Linux system.

## 💻 Audit Analysis

### 1. The Initial Scan
I ran `lynis audit system` to check over 300+ security controls, including kernel hardening, memory protection, and file permissions.

* **Hardening Index:** My initial score was **59**.
* **Findings:** The audit confirmed my Firewall and SSH hardening were active but highlighted several other areas for improvement, such as banner messages and compiler permissions.

<img width="857" height="388" alt="Screenshot 2026-01-11 183705" src="https://github.com/user-attachments/assets/273728c3-7c05-42fa-8a6c-8a46725cd683" />


### 2. Remediation
Based on the audit report, I addressed the missing "Legal Banner" warning.
I modified `/etc/issue.net` to include a warning message for any user attempting to connect.

**Warning Message Added:**
> "UNAUTHORIZED ACCESS PROHIBITED. ALL ACTIVITY IS LOGGED."

This simple change adds a legal layer of defense and slightly improved the system's hardening score upon re-scanning.
