# 🛡️ Day 16: Authentication Log Analysis & Brute Force Detection

## 📝 Executive Summary
After implementing active defense using **Fail2Ban**, I focused on analyzing Linux authentication logs to understand how brute-force login attempts appear from a defender’s perspective. Authentication logs provide visibility into login activity and allow defenders to detect suspicious behavior, identify repeated failed attempts, and verify whether automated protections are functioning correctly.

## 💻 Analysis Steps

### 1. The Objective
I investigated authentication activity by analyzing Linux authentication logs to detect failed login attempts that may indicate brute-force behavior.

Linux records authentication events inside:

```bash
/var/log/auth.log
```

This file contains successful logins, failed login attempts, and invalid user access attempts, making it a primary source of evidence during security investigations.

### 2. Filtering Failed Login Attempts
To isolate suspicious activity, I filtered authentication logs for failed login attempts:

```bash
sudo grep "Failed password" /var/log/auth.log
```

* **Observation:** Multiple failed attempts from the same source IP may indicate automated password guessing.
* **Purpose:** Quickly identify suspicious authentication behavior within large log files.

### 3. Measuring Failed Attempts
To understand the scale of authentication failures, I counted the total number of failed login attempts:

```bash
sudo grep "Failed password" /var/log/auth.log | wc -l
```

* **Reason:** Counting failures helps distinguish between normal user mistakes and potential brute-force activity.
* **Result:** Authentication failures can be quantified and monitored over time.

### 4. Identifying Source IP Addresses
Each failed authentication entry includes the originating IP address.

Example log entry:

```
Failed password for invalid user admin from 192.168.1.25 port 53422 ssh2
```

* **Key Detail:** The source IP identifies where login attempts originate.
* **Security Value:** Enables investigation, blocking, or correlation with other events.

### 5. Validating Active Defense
To confirm that automated protection was functioning correctly, I verified the Fail2Ban status:

```bash
sudo fail2ban-client status sshd
```

Evidence: The status report confirms that repeated failed login attempts triggered automatic banning of the offending IP address, demonstrating the relationship between log monitoring and active defense.
