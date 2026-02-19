# 🛡️ Day 17: Secure Remote Access (SSH Hardening)

## 📝 Executive Summary
Remote access is essential for system administration, but default configurations expose systems to automated attacks. Today, I focused on securing SSH by identifying active services, discovering non-standard ports through network scanning, and establishing a hardened remote connection between machines.

This exercise simulated a real-world scenario where defenders must troubleshoot connectivity issues while validating service exposure from an attacker’s perspective.

---

## 💻 Configuration Steps

### 1️⃣ Network Reconnaissance
From the Kali Linux machine, I performed service discovery to identify open ports on the Ubuntu host.

Command used:
nmap -sV 192.168.93.128

Result:
- Port **2222/tcp** discovered open
- SSH running on a **non-default port**

This demonstrated how administrators reduce automated brute-force attacks by moving SSH away from port 22.

---

### 2️⃣ Understanding the Issue
Initial SSH attempts failed because connections were targeting the default port:

ssh ubuntu@192.168.93.128

Result:
Connection refused.

Root Cause:
SSH service was configured to listen on **port 2222** instead of 22.

---

### 3️⃣ Secure Connection Established
After identifying the correct port, I connected successfully using:

ssh -p 2222 ubuntu@192.168.93.128

This confirmed:
- Network connectivity ✅
- SSH daemon operational ✅
- Proper remote authentication ✅

---

### 4️⃣ Defensive Perspective Validation
From the Ubuntu system, service verification was performed:

sudo ss -tulpn | grep ssh

This allowed validation that sshd was actively listening on the configured port.

---

## 🔐 Security Concepts Learned
- Non-standard SSH ports
- Service enumeration
- Network troubleshooting workflow
- Remote access hardening
- Blue Team verification techniques

---

## 🧠 Key Takeaway
Security troubleshooting requires thinking like both an attacker and a defender. When services fail on expected ports, enumeration becomes critical to understanding real system exposure.

---

## 🏁 Status
✅ Secure SSH access established  
✅ Service enumeration completed  
✅ Remote administration validated
