# 🕵️ Day 3: Service Enumeration

## 📝 Executive Summary
Discovering an open port is not enough; we must understand the service running behind it. Today I focused on **Banner Grabbing** against the SSH service found on Day 2.

## 💻 Commands & Analysis

### 1. Manual Banner Grabbing
```bash
nc 192.168.160.x 22
Why: Netcat (nc) allows us to raw-connect to a port. The service usually sends a "Banner" (text string) identifying itself.

2. Verbose Connection
Bash

ssh -v 192.168.160.x
Why: The -v flag in SSH forces the client to display debug info, revealing the exact protocol versions and encryption methods supported by the server.

Findings:

Protocol: OpenSSH 8.9p1

Auth Methods: Public Key, Password
