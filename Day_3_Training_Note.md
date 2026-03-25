# Day 3 – Linux File System, Grep & Steganography

###  Prepared by: Abdu  
###  Training Program: INSA Weekend Cybersecurity Training  

---

#  Introduction

Day 3 focused on understanding the Linux file system structure, searching techniques using grep, text editors, and an introduction to steganography. These concepts are essential for navigating systems and analyzing hidden data in cybersecurity.

---

#  1. Linux File System Structure

Linux uses a hierarchical (tree-like) structure that starts from the root directory:

/
👉 Everything in Linux exists inside this root.

---

##  Important Directories and Their Uses

| Directory | Purpose | Example |
|----------|--------|--------|
| / | Root directory | /home, /etc |
| /home | User files | /home/kali/Desktop |
| /root | Admin (root user) files | /root/script.sh |
| /bin | Basic system commands | /bin/ls |
| /etc | Configuration files | /etc/passwd |
| /var | Logs and changing data | /var/log/syslog |
| /tmp | Temporary files | /tmp/test.txt |
| /usr | Installed programs | /usr/bin/python |

---

## 🔧 Navigation Commands

pwd            # show current directory
ls             # list files
ls -la         # detailed list (including hidden files)
cd /path       # change directory
cd ..          # go back one level
mkdir test     # create folder
touch file.txt # create file
rm file.txt    # delete file
---

#  2. Grep (Search Tool)

grep is used to search for specific text patterns inside files.

---

##  Basic Usage

grep "text" file.txt
---

##  Important Options

grep -i "text" file.txt     # ignore case
grep -r "text" .            # search recursively
grep -o "pattern" file.txt  # show only matched part
grep -n "text" file.txt     # show line numbers
---

##  Using Pipe with Grep

cat file.txt | grep "flag"
👉 Pipe (|) sends output from one command to another.

---

##  Pattern Example

grep -o "flag{.*}" file.txt
### Explanation:
- flag{} → target pattern  
- . → any character  
- * → repeat many times  

---

#  3. Nano Editor (Beginner Friendly)

Nano is a simple text editor used in the terminal.

---

##  Open File

nano file.txt
---

##  Shortcuts

| Action | Shortcut |
|--------|---------|
| Save | Ctrl + O |
| Exit | Ctrl + X |
| Cut line | Ctrl + K |
| Paste | Ctrl + U |
| Search | Ctrl + W |

---

#  4. Vim Editor (Advanced)

Vim is a powerful and advanced text editor.

---

##  Open File

vim file.txt
---

##  Modes

- Normal mode (default)  
- Insert mode → press i  
- Command mode → press :  

---

## 🔧 Basic Commands

i        # insert mode
Esc      # normal mode
:w       # save
:q       # quit
:wq      # save and quit
:q!      # quit without saving
---

##  Editing

dd       # delete line
yy       # copy line
p        # paste
---

##  Search

/flag
n        # next match
---

#  5. Steganography

Steganography is the technique of hiding secret data inside files such as images, audio, or videos.

---

## 🔧 Common Tools in Kali Linux

### 1. strings
strings file.png
strings file.png | grep -i flag
---

### 2. steghide
steghide extract -sf image.jpg
---

### 3. binwalk
binwalk file.png
binwalk -e file.png
---

### 4. zsteg (for PNG files)
zsteg file.png
---

### 5. exiftool
exiftool file.jpg
---

##  Typical Analysis Workflow

file image.png
strings image.png | grep flag
exiftool image.png
binwalk image.png
binwalk -e image.png
zsteg image.png
steghide extract -sf image.png
---

#  Key Takeaways

- Linux file structure helps organize the system  
- grep is very powerful for searching (especially flags)  
- Nano is simple, Vim is powerful  
- Steganography requires trying multiple tools  

---

#  Practice Done
- Navigated directories using cd, ls  
- Searched for flags using grep  
- Edited files using nano and vim  
- Analyzed files using steganography tools  

---

#  Conclusion

Day 3 strengthened our understanding of Linux navigation, searching techniques, and introduced real cybersecurity practices like steganography. These skills are essential for solving challenges and analyzing hidden data.
