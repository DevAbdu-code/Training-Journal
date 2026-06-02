#  Cybersecurity Networking & Analysis Notes (CTF + Practical Guide)

>  “Understanding the network is understanding the attack.”

---

#  1. Ports & Protocols

##  Two Types of Ports

| Type | Protocol | Characteristics |
|------|----------|----------------|
| TCP Ports | Transmission Control Protocol | Reliable, connection-based |
| UDP Ports | User Datagram Protocol | Fast, connectionless |

---

##  TCP (Connection-Based)

Uses 3-way handshake:
1. SYN → Request  
2. SYN-ACK → Response  
3. ACK → Connection established  

👉 To terminate connection:
- Use RST (Reset flag)

---

##  UDP (Connectionless)

- No handshake  
- Faster but unreliable  
- Uses ICMP responses  

Example:
- Closed port → ICMP "Destination Unreachable"

---

#  2. Firewall Evasion Techniques

##  Problem:
Scanning creates noise (logs & alerts)

---

##  Methods

### 1. Source Port Manipulation
Use trusted ports:
- 53 (DNS)
- 80 (HTTP)

---

### 2. Slow Scanning
Reduce speed to avoid detection

---

### 3. Packet Fragmentation
Break packets to bypass inspection

---

### 4. Decoys
Hide real IP among fake ones

---

>  Best evasion = look normal, not invisible

---

#  3. Version Enumeration

## What is it?
Finding service name and version

Example:
Apache 2.4.49

---

## Why?
- Identify vulnerabilities  
- Match with CVE  
- Plan attacks/defense  

---

#  4. Nmap Scripting Engine (NSE)

## Why Lua?
- Lightweight  
- Fast  
- Easy to embed  
- Secure execution  

---

## Script Location

/usr/share/nmap/scripts

---

#  5. Local vs Remote Scanning

## Local Scan
- Uses ARP (Layer 2)  
- Very fast  

## Remote Scan
- Uses IP routing  
- Slower due to latency & firewall  

---

#  6. Networking Tools

## netstat
Shows open ports & connections  

## MTR
Ping + traceroute combined  

## ss
Faster netstat alternative  

## tcpdump
Packet capture tool  

## tshark
Terminal Wireshark  

---

## Example Commands

tshark -r file.pcap -Y "http"

Meaning:
- -r → read file  
- -Y → filter  

---

tcp.stream eq 3

👉 Filters a specific TCP stream

---

#  7. Wireshark (Terminal)

tshark -r packet.pcap  

Advanced:
tshark -r packet.pcap -T fields -e ip.src  

---

#  8. Windows Event Logs

## Steps:
1. Open Event Viewer  
2. Filter by Event ID  
3. Check time, user, action  

---

## Important Event IDs

| Event ID | Meaning |
|----------|--------|
| 4104 | PowerShell execution |
| 400 | PowerShell start |
| 104 | Log cleared |
| 1102 | Security log cleared |
| 4799 | Group enumeration |

---

👉 EventID = specific system action

---

#  9. Core Concepts (CT2)

## Encapsulation
Data wrapped layer by layer  

## De-encapsulation
Data unwrapped at receiver  

---

## Session (Cookies)
- Stores user identity  
- Used for authentication  

---

## DNS Process
1. User enters domain  
2. DNS resolves IP  
3. Connection starts  

---

## Packet Analysis
Check:
- Headers  
- Payload  

---

#  10. Network Commands

## ifconfig
Shows IP (Linux)

## ipconfig
Shows IP (Windows)

---

## IPv4 vs IPv6

| Feature | IPv4 | IPv6 |
|--------|------|------|
| Size | 32-bit | 128-bit |
| Example | 192.168.1.1 | 2001:db8::1 |

---

## DHCP
Automatically assigns IP addresses  

---

#  11. CVE

## What is CVE?

Common Vulnerabilities and Exposures  

Example:
CVE-2021-44228  

---

## Why Important?
- Identifies vulnerabilities  
- Used in pentesting  
- Helps patch systems  

---

#  12. Advanced (RC2)

- Network reconnaissance  
- Traffic analysis  
- Protocol behavior  
- Attack detection  
- Log correlation  

---

#  FINAL TAKEAWAYS

✔ TCP = reliable, UDP = fast  
✔ Firewall evasion = stealth  
✔ Lua used for Nmap scripting  
✔ Logs + packets = full attack story  
✔ CVE = real-world vulnerabilities  

---

##  Author

Abdu  
Cybersecurity Trainee 
Future Red Teamer  

---

>  “Hackers break systems. Experts understand them.”
