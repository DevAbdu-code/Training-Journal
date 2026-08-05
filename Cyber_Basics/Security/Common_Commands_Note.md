#  Day 2 – Linux Terminal & File Permissions

###  Prepared by: Abdu  
###  Training Program: INSA Weekend Cybersecurity Training  

---

#  Introduction

Day 2 focused on understanding the Linux terminal and basic commands, along with file permissions and how access control works in the system. These skills are essential for navigating and securing Linux systems.

---

#  Basic Linux Terminal Commands

##  1. pwd (Print Working Directory)

- Shows the current directory you are in.

### Example:
pwd
---

##  2. cd (Change Directory)

- Used to move between folders.

### Example:
cd /home/kali
cd ..
cd Desktop
---

##  3. ls (List Files)

- Lists files and directories.

### Example:
ls
---

##  4. ls -l (Detailed List)

- Shows detailed information about files.

### Example:
ls -l
👉 Displays:
- Permissions  
- Owner  
- File size  
- Date  

---

##  5. ls -la (Show Hidden Files)

- Shows all files including hidden ones.

### Example:
ls -la
👉 Hidden files start with . (dot)

---

##  6. cat (View File Content)

- Displays the content of a file.

### Example:
cat file.txt
---

#  File Permissions in Linux

##  What are File Permissions?

File permissions control who can:
- Read (r)  
- Write (w)  
- Execute (x)  

---

## 👥 Types of Users

- Owner (u) → the file creator  
- Group (g) → users in the same group  
- Others (o) → everyone else  

---

##  Permission Symbols

| Symbol | Meaning |
|--------|--------|
| r | Read |
| w | Write |
| x | Execute |

---

##  Numeric Values

| Permission | Value |
|-----------|------|
| Read (r) | 4 |
| Write (w) | 2 |
| Execute (x) | 1 |

👉 These values are combined:

- 7 = rwx (4+2+1)  
- 6 = rw- (4+2)  
- 5 = r-x (4+1)  

---

#  chmod (Change Permissions)

##  What is chmod?

chmod is used to change file permissions.

---

##  Using Numbers

### Example:
chmod 755 file.txt
👉 Meaning:
- Owner → rwx (7)  
- Group → r-x (5)  
- Others → r-x (5)  

---

##  Using Letters

### Example:
chmod u+x file.txt
chmod g-w file.txt
chmod o=r file.txt
👉 Meaning:
- u = user (owner)  
- g = group  
- o = others  

---

#  Example of Permission Output

ls -l
Example:
-rwxr-xr-- 1 kali kali 123 file.txt
👉 Breakdown:
- rwx → owner  
- r-x → group  
- r-- → others  

---

#  Importance of File Permissions

- Protects files from unauthorized access  
- Prevents accidental changes  
- Essential for system security  
- Used heavily in cybersecurity  

---


#  Conclusion

Day 2 introduced essential Linux commands and file permission concepts. Understanding these basics is critical for working in Linux and building a strong foundation in cybersecurity.
