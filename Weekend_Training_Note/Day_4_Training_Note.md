# 🌐 Day 4 – Networking Fundamentals

### 👨‍💻 Prepared by: Abdu  
### 📅 Training Program: INSA Weekend Cybersecurity Training  

---

# 🌐 Introduction

Day 4 focused on networking fundamentals, including types of networks, IP addressing, OSI model, ports, and communication protocols. These concepts are essential for understanding how devices communicate and how attacks occur in networks.

---

# 🔗 What is a Network?

A network is a group of connected computers and devices that communicate and share resources.

---

# 🎯 Purpose of Networking

- File sharing 📂  
- Resource sharing (printers, internet)  
- Communication between devices  
- Data exchange  

---

# 🌍 Types of Network (Geographical)

| Type | Meaning | Example |
|------|--------|--------|
| PAN | Personal Area Network | Bluetooth, phone hotspot |
| LAN | Local Area Network | School or home network |
| MAN | Metropolitan Area Network | City network |
| WAN | Wide Area Network | Internet |

---

# 🧠 IP Address Classes

IP addresses are divided into classes based on the first octet.

---

## 📊 Classes Overview

| Class | Range (1st Octet) | Purpose | Network Bits | Host Bits |
|------|------------------|--------|-------------|-----------|
| A | 1 – 126 | Large networks | 8 | 24 |
| B | 128 – 191 | Medium networks | 16 | 16 |
| C | 192 – 223 | Small networks | 24 | 8 |
| D | 224 – 239 | Multicast | - | - |
| E | 240 – 255 | Experimental | - | - |

---

# 🖥 Server vs Client

## Server:
- Provides services/resources  
- Example: Web server  

## Client:
- Requests services  
- Example: Browser  

---

# 🌍 Public vs Private IP Address

## Public IP:
- Used on the internet  
- Unique globally  

## Private IP:
- Used inside local network  
- Not accessible from internet  

### Common Private IP Ranges:
- 10.0.0.0 – 10.255.255.255  
- 172.16.0.0 – 172.31.255.255  
- 192.168.0.0 – 192.168.255.255  

---

# 🔄 DHCP (Dynamic Host Configuration Protocol)

DHCP automatically assigns IP addresses to devices in a network.

👉 It provides:
- IP address  
- Subnet mask  
- Gateway  

---

# 🧱 OSI Model (Overview)

| Layer | Name |
|------|------|
| 7 | Application |
| 6 | Presentation |
| 5 | Session |
| 4 | Transport |
| 3 | Network |
| 2 | Data Link |
| 1 | Physical |

---

# 🚪 What is a Port?

A port is a communication endpoint used by applications.

👉 Example:
- 80 → HTTP  
- 443 → HTTPS  
- 22 → SSH  

---

# ⚡ TCP vs UDP (VERY IMPORTANT)

## TCP (Transmission Control Protocol)

- Connection-oriented  
- Reliable  
- Slower  
- Ensures data delivery  

### Example:
- Web browsing  
- File transfer  

---

## UDP (User Datagram Protocol)

- Connectionless  
- Faster  
- Not reliable  
- No guarantee of delivery  

### Example:
- Video streaming  
- Online games  

---

## 🔥 Simple Comparison

| Feature | TCP | UDP |
|--------|-----|-----|
| Connection | Yes | No |
| Speed | Slower | Faster |
| Reliability | High | Low |
| Usage | Files, web | Streaming |

---

# 🧬 MAC Address vs IP Address

## MAC Address:
- Physical address  
- Unique to device  
- Example: 00:1A:2B:3C:4D:5E  

## IP Address:
- Logical address  
- Can change  
- Used for communication  

---

# 🧠 Understanding IP Structure

Example IP:
192.168.1.10
👉 First 3 octets (192.168.1):
- Network part  

👉 Last octet (10):
- Host (device)  

---

# 💡 Key Takeaways

- Networks allow communication between devices  
- IP addresses identify devices  
- TCP is reliable, UDP is fast  
- Ports act like doors for communication  
- MAC = physical identity, IP = logical identity  

---

# 🚀 Conclusion

Day 4 provided essential knowledge about networking, which is the backbone of cybersecurity. Understanding how networks work helps in both attacking and defending systems.
