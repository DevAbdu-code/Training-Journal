#  Windows Event Logs: Forensic Analysis & Incident Response

>  *“Every action in Windows leaves a trace — logs are the footprints of attackers.”*

---

## 📂 1. Core Windows Log Categories

Windows stores critical logs in:

C:\Windows\System32\winevt\Logs\

These logs are essential for digital forensics, threat detection, and incident response.

|  Log Type |  Description |  Forensic Value |
|------------|--------------|------------------|
| System | Events from OS components (drivers, services, kernel). | Detect shutdowns, crashes, and log clearing attempts. |
| Security | Tracks authentication, access, and privilege usage. | Detect brute-force attacks, privilege escalation, lateral movement. |
| Application | Events from installed applications. | Identify crashes, vulnerabilities, or exploited software. |

---

##  2. Critical Event IDs for Security Monitoring

These Event IDs are gold  in cybersecurity investigations:

---

###  A. Anti-Forensics (Hiding Tracks)

| Event ID | Meaning | Why It Matters |
|----------|--------|---------------|
| 104 | System log cleared |  Attacker trying to erase evidence |
| 1102 | Security log cleared |  Very strong indicator of compromise |

---

###  B. Execution & Scripting (PowerShell Attacks)

| Event ID | Meaning | Why It Matters |
|----------|--------|---------------|
| 400 | PowerShell engine started | Detect downgrade attacks |
| 4104 | Script block execution |  Shows actual executed code |

 Attackers often:
- Use Base64 encoding  
- Obfuscate scripts  
- Execute payloads silently  

👉 This log helps reveal:
- Malware (e.g., Emotet, Cobalt Strike)  
- Reverse shells  
- Hidden commands  

---

###  C. Reconnaissance & Enumeration

| Event ID | Meaning | Why It Matters |
|----------|--------|---------------|
| 4799 | Group membership enumeration | Attacker checking admin privileges |

💡 This is usually early-stage attack behavior.

---

###  D. Authentication & Access

| Event ID | Meaning | Why It Matters |
|----------|--------|---------------|
| 4624 | Successful login | Track user access |
| 4625 | Failed login | Detect brute-force attacks |

 Important Logon Types:
- Type 2 → Local login  
- Type 3 → Network login  
- Type 10 → Remote Desktop (RDP)  

---

###  E. Persistence & Account Manipulation

| Event ID | Meaning | Why It Matters |
|----------|--------|---------------|
| 4720 | New user created |  Possible attacker persistence |
| 4722 | User enabled | Reactivating accounts |
| 4732 | Added to admin group | Privilege escalation |

---

##  3. Forensic Analysis Workflow

###  Step 1: Filter Logs
Use Event Viewer → Filter Current Log  
Focus on:
4104, 4625, 1102, 4720  

---

###  Step 2: Deep Inspection
Switch to XML View and look for:
- Hidden commands  
- Encoded payloads  
- Suspicious parameters  

---

###  Step 3: Trace the Source
Identify:
- UserSID  
- ProcessID  
- Account Name  

👉 Helps answer: “Who did this?”

---

###  Step 4: Decode Payloads
If you find encoded data:

Example:
Base64 → Decode using CyberChef  

Tools:
- CyberChef  
- PowerShell  
- base64 -d (Linux)  

---

###  Step 5: Correlate Events

Example chain:
4625 → 4624 → 4720  

👉 Means:
Failed login → Success → New user created  
 Strong attack pattern  

---

##  4. Quick Reference Table

|  Category |  Event ID |  Meaning |
|------------|------------|-----------|
| Logs Cleared | 104 / 1102 | Evidence tampering |
| PowerShell | 4104 | Script execution |
| Login Success | 4624 | User access |
| Login Failure | 4625 | Brute force |
| User Created | 4720 | Persistence |
| Enumeration | 4799 | Recon activity |

---

## ⚔️ 5. Real Attack Scenario (CTF Style)

 Example:

1. Attacker scans system  
2. Runs PowerShell payload (4104)  
3. Brute-force login (4625)  
4. Gains access (4624)  
5. Creates new user (4720)  
6. Clears logs (1102)  

👉 This forms a complete attack chain

---

##  6. Summary
✔ Windows logs are critical forensic evidence  
✔ Event IDs tell a story of attacker behavior  
✔ Always correlate multiple logs  
✔ PowerShell logs are very powerful for detection  
✔ Log clearing =  HIGH ALERT  

---

##  Author

Abdu  
Cybersecurity Trainee   
Future Ethical Hacker   

---

>  “Logs never lie — attackers just try to hide them.”
