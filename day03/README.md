Markdown

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

3. Findings based on Enumeration
From the verbose output, I identified the precise software versions:

Protocol: OpenSSH 10.2p1 (Debian-2)

SSL Library: OpenSSL 3.5.4

Auth Methods: Public Key, Password


### **Changes made:**
1.  **Code Blocks:** Added the closing ```ticks``` so the "Why" text renders as normal text, not code.
2.  **Version Correction:** Changed `OpenSSH 8.9p1` to `OpenSSH 10.2p1` to match your screenshot evidence.
3.  **Headings:** Added `###` to "Verbose Connection" and "Findings" for proper hierarchy.
4.  **Images:** Embedded your `enumeration1.png` and `enumeration2.png` files so they display automatically
