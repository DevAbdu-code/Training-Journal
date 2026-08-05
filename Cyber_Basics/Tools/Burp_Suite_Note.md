#  Burp Suite Basics – Practical Notes (Kali Linux)

> Hands-on notes for learning Burp Suite workflow for web testing and CTF practice.

---

##  Overview
This repo summarizes core features and a practical workflow using Burp Suite.

---

##  Environment
- Kali Linux
- Burp Suite (Community)
- Firefox + FoxyProxy (127.0.0.1:8080)

---

##  Setup
1. Configure FoxyProxy → 127.0.0.1:8080
2. Burp → Proxy → Intercept: ON
3. Use Open Browser or configured Firefox

---

##  Core Tabs

###  Target
- Site map of the application
- Define Scope to limit testing

###  Proxy
- Intercept: capture requests
- Forward: send to server
- Drop: block request
- HTTP History: all traffic log

####  Views
| View | Meaning |
|------|--------|
| Raw  | Exact HTTP bytes |
| Pretty | Formatted view |
| Hex | Byte-level |

---

###  Repeater
- Manually edit & resend a request
- Best for testing input handling

---

###  Intruder (Automation)

####  What is a Payload?
> Payload = the data you inject into a request to test behavior
Examples:
- usernames/passwords
- fuzz strings
- SQL/XSS test inputs

####  Payload Controls
- Add → insert custom values (e.g., admin, test, ' OR 1=1)
- Clear → remove all payloads (reset list)
- Load → import from a wordlist file (e.g., rockyou.txt)

####  Attack Types

| Type | Meaning | When to Use |
|------|--------|------------|
| Sniper | One position, tries payloads one by one | Test a single parameter |
| Battering Ram | Same payload applied to all positions | When inputs must match |
| Pitchfork | Multiple lists, used in parallel (1-to-1) | username ↔ password pairs |
| Cluster Bomb | All combinations of multiple lists | brute-force combos |

---

###  Collaborator
- Detects out-of-band issues (e.g., blind SSRF)

---

###  Decoder
- Encode/decode data (Base64, URL, Hex)

---

##  Practical Workflow

1. Intercept request (Proxy)  
2. Inspect in HTTP History  
3. Send to Repeater  
4. Modify parameters  
5. Send to Intruder (if automation needed)  
6. Decode/encode if required  

---

##  Example (Repeater Test)

➡ Send to Repeater  
➡ Modify:

`http
GET /login?user=admin HTTP/1.1
Host: example.com
---
➡ Inject test input:
---
GET /login?user=admin' OR '1'='1 HTTP/1.1
Host: example.com

---
➡ Observe response (status, content changes)
