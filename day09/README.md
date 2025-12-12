# 🛡️ Day 9: Privilege Escalation (Capabilities)

## 📝 Executive Summary
Linux "Capabilities" were designed to make systems safer by splitting up the root privileges into smaller segments. However, assigning the `CAP_SETUID` capability to a programming language interpreter (like Perl, Python, or Tar) is effectively the same as giving it SUID Root. Today, I exploited this misconfiguration.

## 💻 Technical Analysis

### 1. Enumeration (getcap)
Instead of looking for SUID bits, I searched for set capabilities using the `getcap` tool.

```bash
/sbin/getcap -r / 2>/dev/null
Finding: /usr/bin/perl has cap_setuid+ep.

Risk: This capability allows the binary to change its own Process User ID (UID). I can instruct Perl to change its UID to 0 (Root).

2. The Exploit
I used a simple Perl script to import the POSIX module, set the user ID to 0, and execute a system shell.

Bash

perl -e 'use POSIX qw(setuid); POSIX::setuid(0); exec "/bin/sh";'
3. Impact (Root Access)
The command succeeded, dropping me into a root shell.
