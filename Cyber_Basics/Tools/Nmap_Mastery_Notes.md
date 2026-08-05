#  Nmap Mastery Notes — Cybersecurity Training

 Author: Abdu  
 Focus: Network Scanning, Enumeration & Analysis  

---

#  1. What is Nmap?

Nmap (Network Mapper) is a powerful open-source tool used for:

✔ Network discovery  
✔ Port scanning  
✔ Service detection  
✔ OS detection  
✔ Security auditing  

---

# 🎯 2. What is Nmap Used For?

- Discover live hosts
- Identify open ports
- Detect running services
- Identify OS and versions
- Find vulnerabilities (with NSE)

---

# 🌐 3. OSI Layers Used by Nmap (UPDATED ✅)

| Layer | Role |
|------|------|
| Layer 2 (Data Link) | ARP scanning (local network discovery) |
| Layer 3 (Network) | Host discovery (IP, ICMP) |
| Layer 4 (Transport) | Port scanning (TCP/UDP) |
| Layer 7 (Application) | Service detection |

---

##  Layer 2 Explanation (VERY IMPORTANT)

👉 Nmap uses ARP (Address Resolution Protocol) on local networks:

Example:
nmap -sn 192.168.1.0/24
👉 Instead of ICMP:
- It sends ARP requests  
- Faster and more accurate on LAN  

✔ Works only in local network  
✔ Cannot be routed over internet  

---

# 🔍 4. TCP Scan (Very Important)

## SYN Scan (-sS)
- Half-open scan
- Sends SYN → receives SYN-ACK → sends RST
- Fast & stealthy

## TCP Connect Scan (-sT)
- Full handshake (SYN → SYN-ACK → ACK)
- Slower but reliable
- Logged by systems

---

# 🧪 5. UDP Scan (-sU)

- No handshake
- Open ports → no response
- Closed ports → ICMP error
- Slow and less reliable

---

# 🐢 6. Why UDP Scan is Slow

- No response = must wait
- Requires retries
- ICMP rate limiting
- Firewall interference

---

# 🖥️ 7. OS Detection (-O)

- Uses fingerprinting
- Checks:
  - TTL
  - TCP behavior
  - Packet responses
- Matches with database

---

# ⚙️ 8. NSE (Nmap Scripting Engine)

Allows advanced operations:

- Vulnerability scanning
- Brute-force attacks
- Service interaction

### Example:
nmap --script vuln target
---

# 🧰 9. Common Nmap Flags

| Flag | Function |
|------|--------|
| -sS | SYN scan |
| -sT | TCP connect |
| -sU | UDP scan |
| -sV | Version detection |
| -O  | OS detection |
| -A  | Aggressive scan |
| -p  | Specify ports |
| -T  | Speed control |
| -sC | Default scripts |

---

# ⚡ 10. Timing Template (-T)

| Level | Speed |
|------|------|
| T0 | Very slow |
| T3 | Normal |
| T5 | Very fast |

---

## ❌ Demerits of -T5 (Very Important)

Using -T5 can:

- ❗ Trigger IDS/IPS detection
- ❗ Cause packet loss
- ❗ Reduce accuracy
- ❗ Miss open ports
- ❗ Overload network

👉 Use carefully in real environments!

---

# 🚫 11. Port States

| State | Meaning |
|------|--------|
| Open | Service is running |
| Closed | No service |
| Filtered | Blocked by firewall |

---

# 🛡️ 12. Firewall Evasion Techniques

| Technique | Description |
|----------|------------|
| -f | Fragment packets |
| -D | Use decoys |
| --source-port | Fake source port |
| -T0 | Slow scan |
| --randomize-hosts | Random targets |

---

# 🎄 13. Xmas Scan (-sX)

- Uses flags: FIN + PSH + URG
- Closed → RST
- Open → No response
- Works best on Linux/Unix

---
# 🧠 14. What is SMAP?

👉 SMAP (Simplified Network Mapper) is a lightweight and faster alternative concept/tool related to network scanning.

---

## 🔍 Key Idea

SMAP is designed to:
- Perform fast port scanning
- Provide simplified output
- Reduce complexity compared to advanced tools

---

## ⚙️ Features

- Faster scanning (less detailed than Nmap)
- Simple interface
- Focus on speed over deep analysis

---

## ⚖️ SMAP vs Nmap

| Feature | SMAP | Nmap |
|--------|------|------|
| Speed | Faster | Moderate |
| Detail | Low | Very High |
| Complexity | Simple | Advanced |
| Use Case | Quick scan | Deep analysis |

---

## 🧠 When to Use SMAP

👉 Use SMAP when:
- You need quick results  
- You don’t need detailed analysis  
- You are doing initial reconnaissance  

---

## ⚠️ Limitation

- Not as powerful as Nmap  
- Limited features  
- Less accurate in complex environments  

---

## 🎯 Summary

> SMAP is a simplified and faster scanning approach/tool used for quick reconnaissance, while Nmap provides deeper and more advanced network analysis.

# ⚔️ 15. Masscan vs Rustscan

## 🚀 Masscan
- Extremely fast scanner
- Can scan entire internet
- Less accurate
- No deep analysis

## 🦀 Rustscan
- Fast + intelligent
- Finds open ports quickly
- Hands results to Nmap

### Example:
rustscan -a 192.168.1.5
---

# 🧟 16. Zombie Host (Idle Scan)

👉 A zombie = an idle machine used to scan target indirectly

### How it works:
- Attacker → Zombie → Target
- Target thinks zombie is scanning

✔ Anonymous scanning  
✔ Hard to trace attacker  

---

# 🧪 17. Common Nmap Practice Labs

🔥 Platforms:

- TryHackMe
- Hack The Box
- OverTheWire (Bandit)
- VulnHub

---

# 📚 18. What is CVE?

👉 CVE = Common Vulnerabilities and Exposures

A unique ID for known security vulnerabilities.

## 🔗 Related Concepts

### 🔹 CVSS (Common Vulnerability Scoring System)
- Measures severity (0 – 10)
- Example:
  - 9.8 = Critical

---

### 🔹 Exploit
👉 Code or technique used to take advantage of a vulnerability

---

### 🔹 Patch
👉 A fix released by developers to remove vulnerability

---


> Nmap is a powerful network scanning tool that operates across multiple OSI layers, enabling cybersecurity professionals to discover hosts, analyze ports, detect services, identify operating systems, and assess vulnerabilities efficiently.

---


💡 “Scanning is not just sending packets —  
it is understanding how systems respond.”

---

# 🔥 Advanced Topic — Firewall Evasion & Noise Management

---

# 🛡️ 1. Why Firewall Evasion Matters

When performing scans using tools like Nmap:

👉 Every scan generates network traffic (noise)  
👉 This noise is often:
- Logged   
- Monitored   
- Analyzed   

---

## ⚠️ Problem

> “Loud scans = easy detection”

---

# ⚔️ 2. Common Firewall Evasion Techniques (Red Team Focus)

---

## 🔹 1. Packet Fragmentation (-f)

nmap -f 192.168.1.5
👉 Breaks packets into smaller pieces  
👉 Some firewalls fail to reassemble them  

---

## 🔹 2. Decoy Scan (-D)

nmap -D RND:5 192.168.1.5
👉 Sends scan from multiple fake IPs  
👉 Hides real attacker  

---

## 🔹 3. Source Port Manipulation

nmap --source-port 53 192.168.1.5
👉 Appears like trusted traffic (e.g., DNS)  

---

## 🔹 4. Slow Scanning (-T0 / -T1)

nmap -T0 192.168.1.5
👉 Very slow scan  
👉 Avoids detection thresholds  

---

## 🔹 5. Randomize Hosts

nmap --randomize-hosts 192.168.1.0/24
👉 Prevents pattern detection  

---

## 🔹 6. Idle Scan (Zombie Scan)

nmap -sI zombie_ip target_ip
👉 Uses a third-party (zombie)  
👉 Target never sees real attacker  

---

---

# 🔴 3. Red Team Perspective (Stealth & Low Noise)

---

## 🎯 Goal:
> Stay undetected while gathering information

---

## 🔥 Techniques to Reduce Noise

### ✔ Use SYN Scan instead of full scan
nmap -sS target
👉 Avoids full connection logging  

---

### ✔ Scan specific ports only
nmap -p 22,80,443 target
👉 Reduces traffic volume  

---

### ✔ Slow down scan speed
nmap -T1 target
👉 Blends with normal traffic  

---

### ✔ Use decoys
nmap -D RND:10 target
👉 Confuses defenders  

---

### ✔ Avoid aggressive scan
❌ Avoid:
nmap -A target
👉 Too noisy  

---

### ✔ Combine tools intelligently
- Use Rustscan → find ports  
- Use Nmap → deep scan only necessary ports  

---

## 🧠 Red Team Strategy

> “Scan less, but scan smart.”

---

---

# 🔵 4. Blue Team Perspective (Detection & Defense)

---

## 🎯 Goal:
> Detect, analyze, and stop suspicious scanning activity

---

## 🔍 Signs of Nmap Scanning

- Multiple ports scanned quickly  
- Unusual TCP flags (NULL, Xmas)  
- Repeated SYN packets  
- Strange timing patterns  

---

---

## 🛡️ Defense Techniques

---

### ✔ Use Firewall Rules

- Block suspicious IPs  
- Limit repeated connections  

---

---

### ✔ Intrusion Detection Systems (IDS)

Examples:
- Snort  
- Suricata  

👉 Detect scanning patterns  

---

---

### ✔ Log Monitoring

Check:
- Connection attempts  
- Port scanning patterns  
- Failed connections  

---

---

### ✔ Rate Limiting

👉 Limit number of requests per second  

---

---

### ✔ Packet Inspection

👉 Detect:
- Fragmented packets  
- Fake source ports  
- Abnormal flags  

---

---

##  Blue Team Strategy

> “Detect patterns, not just packets.”

---

---

# ⚖️ 5. Red vs Blue Summary

| Role | Focus |
|------|------|
| 🔴 Red Team | Stay hidden & reduce noise |
| 🔵 Blue Team | Detect patterns & block attacks |

---

---

# 🚨 6. Key Insight

👉 Scanning is a battle of intelligence:

- Red Team → hides behavior  
- Blue Team → detects behavior  

---

---

# 🎤 FINAL SUMMARY

> Firewall evasion techniques are critical in red teaming to bypass detection mechanisms, while blue teams rely on monitoring, logging, and pattern recognition to detect and prevent such stealthy scanning activities.

---

### Example:
CVE-2021-44228
---
