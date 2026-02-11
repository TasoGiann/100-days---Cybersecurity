Yes, I remember — you want the README written in the same structured lab style as your previous days:

✅ Clear title
✅ Executive Summary
✅ Technical / Configuration steps
✅ Numbered sections
✅ Short explanations (not long essays)
✅ Written like a real security lab report for recruiters

Below is Day 16, formatted exactly to match your Day 14 / Day 15 style, so it looks consistent across your GitHub.

You can paste this directly into:

day16/README.md

🛡️ Day 16: Authentication Log Analysis & Brute Force Detection
📑 Executive Summary

After implementing active defense mechanisms using Fail2Ban, I focused on analyzing Linux authentication logs to understand how brute-force login attempts appear from a defender’s perspective.

Authentication logs provide visibility into login activity and allow defenders to detect suspicious behavior, identify repeated failed login attempts, and verify whether automated defensive controls are functioning correctly.

This exercise demonstrates how log analysis supports threat detection and incident investigation in a Blue Team environment.

💻 Analysis Steps
1. The Objective

The goal of this exercise was to:

Identify failed authentication attempts

Detect potential brute-force behavior

Extract source IP addresses from logs

Validate that Fail2Ban successfully blocks malicious activity

Linux stores authentication activity in:

/var/log/auth.log

This file contains both successful and failed login attempts, making it a primary source of evidence during investigations.

2. Filtering Failed Login Attempts

To isolate suspicious activity, authentication logs were filtered for failed login attempts:

sudo grep "Failed password" /var/log/auth.log

This allowed failed authentication events to be separated from normal system activity.

Repeated failures originating from the same IP address may indicate automated password guessing or brute-force attacks.

3. Counting Authentication Failures

To evaluate the scale of failed login activity, the total number of failed attempts was counted:

sudo grep "Failed password" /var/log/auth.log | wc -l

Counting failures helps determine whether login attempts represent normal user errors or suspicious automated behavior.

4. Identifying Source IP Addresses

Each authentication failure entry includes the originating IP address.

Example:

Failed password for invalid user admin from 192.168.1.25 port 53422 ssh2


The source IP provides valuable information for investigation and allows defenders to trace the origin of suspicious activity.

5. Validating Active Defense (Fail2Ban)

To confirm that automated protection was functioning correctly, Fail2Ban status was checked:

sudo fail2ban-client status sshd

The output confirmed that repeated failed login attempts triggered automatic banning of the offending IP address, demonstrating the relationship between detection and automated response.

📊 Key Observations

Authentication logs provide detailed insight into system access attempts.

Multiple failed login attempts indicate possible brute-force activity.

Log filtering significantly improves investigation efficiency.

Fail2Ban successfully blocks repeated malicious authentication attempts.

📸 Screenshots

Viewing authentication logs (auth.log)

Failed login filtering output

Failed login attempt count

Example failed login entry showing source IP

Fail2Ban status confirming banned IP
