# 🔐 Authentication, Authorization & Brute Force – Complete Guide

![Cybersecurity](https://img.shields.io/badge/Field-Cybersecurity-blue)
![Topic](https://img.shields.io/badge/Focus-Authentication%20%26%20Access%20Control-orange)
![Level](https://img.shields.io/badge/Level-Beginner%20→%20Advanced-green)

> A complete, structured, and practical guide to authentication, authorization, brute force attacks, and password security fundamentals.

---

#  1. Core Idea of Web Security

Every web application must answer **two critical questions**:

- ❓ **Who are you?** → Authentication  
- ❓ **What are you allowed to do?** → Authorization  

---

#  2. Authentication vs Authorization

##  Authentication (Identity Verification)

> Authentication = **Proving who you are**

###  Examples:
- Password
- PIN
- Fingerprint
- OTP (SMS code)

###  Three Authentication Factors:

| Factor | Description | Example |
|------|------------|--------|
| Something you **KNOW** | Secret knowledge | Password, PIN |
| Something you **HAVE** | Physical object | Phone, token |
| Something you **ARE** | Biometrics | Fingerprint, face |

---

## 🛡️ Authorization (Permission Control)

> Authorization = **What you are allowed to do**

- Happens **AFTER authentication**
- Controls access to:
  - Pages
  - Data
  - Actions

###  Example:
- Admin → Can delete users  
- User → Can only view profile  

---

##  Side-by-Side Comparison

| Feature | Authentication | Authorization |
|--------|---------------|--------------|
| Question | Who are you? | What can you do? |
| Timing | First (login) | After login |
| Failure | HTTP 401 | HTTP 403 |
| Data Used | Password, biometrics | Roles, permissions |
| Common Flaw | Weak passwords | Privilege escalation, IDOR |

---

#  3. Brute Force Concept

> A **trial-and-error attack** to guess credentials.

###  Key Idea:
- No intelligence  
- Just **trying many combinations**

###  Analogy:
> Like trying all combinations on a lock (0000 → 9999)

---

#  4. Types of Brute Force Attacks

| Type | How it Works | Speed | Effectiveness |
|------|------------|------|--------------|
| **Simple Brute Force** | Tries all combinations | Slow | Weak passwords only |
| **Dictionary Attack** | Uses common password list | Fast | Very effective |
| **Credential Stuffing** | Uses leaked credentials | Fastest | Extremely effective |

---

#  5. What Makes Brute Force Possible?

Brute force succeeds when systems are weak:

- ❌ No rate limiting  
- ❌ No account lockout  
- ❌ No CAPTCHA  
- ❌ Weak password policy  

👉 Example:
- Server allows **1000 login attempts/minute**

---

#  6. Role of Error Messages

##  Information Leakage

Error messages can reveal:

- Valid usernames  
- System behavior  
- Server details  

---

##  Example:

- ❌ “Username not found” → username invalid  
- ❌ “Incorrect password” → username valid  

👉 This allows **enumeration**

---

##  Secure Practice:

> Always use:
Invalid username or password

---

#  7. Enumeration (VERY IMPORTANT)

> Enumeration = **Discovering valid data from the system**

### Examples:
- Valid usernames  
- Hidden directories  
- API endpoints  

👉 Often done using:
- Error messages  
- Response differences  

---

#  8. Brute Force Countermeasures

To stop attacks:

- ✅ Rate limiting  
- ✅ Account lockout  
- ✅ CAPTCHA  
- ✅ Multi-Factor Authentication (MFA)  
- ✅ Strong password policy  

---

#  9. Password Storage: Hashing vs Encryption

---

##  Hashing

> One-way transformation of data

###  Key Features:
- ❌ Cannot reverse  
-  Same input → same hash  

###  Example:
password → 5e884898da28047151d...

---

##  Encryption

> Two-way transformation using a key

###  Key Features:
-  Can decrypt  
-  Requires key  

---

##  Comparison

| Feature | Hashing | Encryption |
|--------|--------|-----------|
| Direction | One-way | Two-way |
| Reversible | ❌ No | ✅ Yes |
| Key Needed | ❌ No | ✅ Yes |
| Password Use | ✅ YES | ❌ NO |

---

#  10. Why Passwords Must Be Hashed

### ❌ If encrypted:
- Key must be stored  
- If key is stolen → all passwords exposed  

###  Hashing:
- No key needed  
- Cannot reverse  

👉 **Rule: Always hash passwords**

---

#  11. Salting (VERY IMPORTANT)

> Adding random data before hashing

###  Example:
Password: hunter2
Salt: x7$kL9#m
Final: hunter2x7$kL9#m → hash
---

###  Benefit:
- Same password ≠ same hash  
- Stops rainbow table attacks  

---

#  12. Modern Secure Algorithms

##  DO NOT USE:
- MD5  
- SHA-1  
- SHA-256 (too fast)

---

##  USE:
- bcrypt  
- Argon2  
- PBKDF2  

###  Why?
> Slow = Secure (hard for brute force)

---

# 🏁 Final Summary

- Authentication = identity  
- Authorization = permissions  
- Brute force = trial-and-error attack  
- Error messages can leak data  
- Hashing is required for passwords  
- Salting prevents hash attacks  
- Use modern slow algorithms  

---

#  Author

**Abdu**  
Cybersecurity Student | Ethical Hacking Enthusiast  

---

#  Support

If you found this helpful:
-  Star this repository  
-  Share with others  

---

#  Disclaimer

This content is for **educational purposes only**.  
Practice only in legal labs and authorized environments.
