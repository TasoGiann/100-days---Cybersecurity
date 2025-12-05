# 🔍 Day 2: Network Reconnaissance

## 📝 Executive Summary
With the lab active, I began the first phase of the kill chain: **Reconnaissance**. I used `ping` to verify reachability and `nmap` to identify active services on the target.

## 💻 Commands & Analysis

### 1. Reachability Check
```bash
ping -c 4 192.168.160.x
Why: Before running heavy scans, we must confirm the host is up.

Result: Host is active.

2. Service Scanning
Bash

nmap -sV 192.168.160.x
Why: nmap reveals which "doors" (ports) are open. The -sV flag specifically enumerates the Version of the service, which is critical for finding vulnerabilities.

Findings:

Port 22 (Open): SSH (OpenSSH 9.6p1 Ubuntu)

OS Detection: Linux Kernel
