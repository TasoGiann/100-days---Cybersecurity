# 💥 Day 5: Brute Force Attack (Hydra)

## 📝 Executive Summary
To simulate a real-world attack against weak credentials, I used **Hydra** to perform a dictionary attack against the SSH service. This demonstrates why strong passwords and rate limiting are critical defenses.

## 💻 Attack Workflow

### 1. Creating the Wordlist
I created a custom wordlist `creds.txt` containing common weak passwords (`123456`, `password`, `toor`).

![Wordlist](./screenshots/creds.txt.png)

### 2. Launching the Attack
```bash
hydra -l ubuntu -P creds.txt ssh://192.168.160.x -t 4 -V
Why:

-l ubuntu: Target specific username.

-P creds.txt: Path to password list.

-t 4: Run 4 parallel tasks (speed).

ssh://...: Protocol and target.

3. Result
Hydra successfully cracked the password: ubuntu.
