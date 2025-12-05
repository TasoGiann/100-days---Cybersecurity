# 🏗️ Day 1: Lab Initialization

## 📝 Executive Summary
Today I successfully built an isolated cybersecurity home lab. The goal was to create a safe, "Host-Only" environment where I can practice offensive techniques without risking exposure to the public internet or my home network.

## 🛠️ Infrastructure Setup
| Component | Specification | Role |
| :--- | :--- | :--- |
| **Hypervisor** | VMware Workstation | Lab Management |
| **Attacker** | Kali Linux (Rolling) | Red Team Operations |
| **Target** | Ubuntu Server 24.04 | Victim Machine |
| **Network** | Host-Only (`vmnet1`) | Traffic Isolation |

## ⚙️ Configuration Details
* **Network Mode:** Host-Only (No Internet Access for Victim)
* **Subnet:** `192.168.160.0/24`
* **Kali IP:** `192.168.160.x`
* **Target IP:** `192.168.160.x`

## 📸 Verification
*Verified connectivity between VMs using `ip a` and `ping` to ensure the isolated network is functional.*
*(Screenshots of your `ip a` command go here in the `images/` folder)*
