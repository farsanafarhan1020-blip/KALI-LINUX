<div align="center">

# 🐉 Kali Linux Masterclass
## 📘 Phase 1 – Linux Fundamentals

# 08 - Linux Networking Fundamentals

*"Networking is the language computers use to communicate. Understanding it is the first step toward mastering cybersecurity."*

![Linux](https://img.shields.io/badge/Linux-Networking-FCC624?style=for-the-badge&logo=linux)
![Kali](https://img.shields.io/badge/Kali-Linux-557C94?style=for-the-badge&logo=kalilinux)
![Networking](https://img.shields.io/badge/Networking-Essentials-blue?style=for-the-badge)
![Cybersecurity](https://img.shields.io/badge/Cybersecurity-Foundation-red?style=for-the-badge)

</div>

---

# 📚 Table of Contents

- Introduction
- What is Networking?
- Types of Networks
- Network Interfaces
- IP Address
- IPv4 vs IPv6
- Public vs Private IP Addresses
- MAC Address
- IP Address vs MAC Address
- Hostname
- The `ip` Command
- Understanding Interface Information
- Routing
- Default Gateway
- Network Architecture
- DNS Basics
- DNS Resolution Process
- Best Practices
- Cybersecurity Perspective

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

✅ Understand computer networking fundamentals

✅ Identify network interfaces

✅ Understand IP and MAC addresses

✅ Use Linux networking commands

✅ Understand routing and gateways

✅ Learn how DNS works

✅ Build a strong networking foundation for cybersecurity

---

# 🌟 Introduction

Every cybersecurity tool depends on networking.

Whether you're using:

- Nmap
- Wireshark
- Burp Suite
- Metasploit
- Hydra
- SSH
- FTP

they all communicate through computer networks.

Understanding networking means understanding **how attackers and defenders communicate across systems.**

---

# 🌐 What is Networking?

A **computer network** is a collection of devices connected together so they can exchange information.

Examples:

- Laptop ↔ Laptop
- Laptop ↔ Router
- Phone ↔ Wi-Fi
- Computer ↔ Server
- Server ↔ Internet

The Internet itself is simply the **largest computer network in the world**.

---

# 🏠 Real-Life Analogy

Imagine sending a letter.

```
You
 ↓
Post Office
 ↓
Road Network
 ↓
Destination House
```

Networking works similarly.

```
Computer
 ↓
Router
 ↓
Internet
 ↓
Destination Computer
```

Instead of letters, computers exchange **packets**.

---

# 🌍 Types of Networks

## LAN (Local Area Network)

A small network within a limited area.

Examples:

- Home Wi-Fi
- Office Network
- School Lab

```
Laptop
   │
Phone ─ Router ─ Printer
   │
Desktop
```

---

## MAN (Metropolitan Area Network)

Connects multiple LANs within a city.

Example:

```
Office A
     │
City Network
     │
Office B
```

---

## WAN (Wide Area Network)

Connects networks across countries and continents.

Example:

```
India
   │
Internet
   │
USA
```

The Internet is the biggest WAN.

---

# 🔌 Network Interfaces

A **Network Interface** is the connection through which your computer communicates.

Think of it as a **door**.

Every packet entering or leaving your system uses one of these interfaces.

Examples include:

- Ethernet
- Wi-Fi
- Virtual Machine Adapter
- VPN Interface
- Loopback Interface

---

# 🖥 Common Linux Interfaces

Older naming:

```
eth0
eth1
wlan0
```

Modern Linux naming:

```
enp0s3

ens33

wlp2s0
```

Loopback:

```
lo
```

---

# 🔁 Loopback Interface

The loopback interface allows your computer to communicate with itself.

```
127.0.0.1
```

or

```
localhost
```

Think of it as talking to yourself in a mirror.

Applications often use loopback for local communication.

---

# 🌐 IP Address

An **IP Address (Internet Protocol Address)** uniquely identifies a device on a network.

Example:

```
192.168.1.25
```

Without an IP address, computers wouldn't know where to send information.

Think of it as your home's mailing address.

---

# 🧮 Structure of an IPv4 Address

Example:

```
192.168.1.25
```

It contains **four numbers**, separated by dots.

Each number ranges from:

```
0 – 255
```

Each section is called an **octet**.

```
192

168

1

25
```

---

# 🌍 IPv4 vs IPv6

## IPv4

Example:

```
192.168.1.50
```

32-bit address

Approximately **4.3 billion** addresses.

---

## IPv6

Example:

```
2001:db8:85a3::8a2e:370:7334
```

128-bit address

Supports an almost unlimited number of devices.

Modern networks increasingly use IPv6.

---

# 🌎 Public vs Private IP

## Public IP

Assigned by your Internet Service Provider (ISP).

Visible on the Internet.

Example:

```
49.36.xxx.xxx
```

---

## Private IP

Used inside homes and offices.

Common ranges:

```
10.0.0.0/8

172.16.0.0 – 172.31.255.255

192.168.0.0/16
```

Private IP addresses cannot be accessed directly from the Internet.

---

# 🏷 MAC Address

Every Network Interface Card (NIC) has a unique hardware address.

Example:

```
00:1A:2B:3C:4D:5E
```

A MAC address is assigned by the manufacturer.

Unlike IP addresses, MAC addresses rarely change.

Think of it as your computer's fingerprint.

---

# ⚖ IP Address vs MAC Address

| IP Address | MAC Address |
|------------|-------------|
| Logical Address | Physical Address |
| Can change | Usually permanent |
| Used across networks | Used within local networks |
| Assigned by network | Assigned by manufacturer |

---

# 🖥 Hostname

A hostname is simply your computer's name.

Example:

```
kali
```

View hostname:

```bash
hostname
```

Another useful command:

```bash
hostnamectl
```

This displays:

- Hostname
- Operating System
- Kernel Version
- Architecture

---

# 📡 The `ip` Command

Modern Linux uses the **iproute2** package.

The most important command:

```bash
ip a
```

or

```bash
ip addr
```

Example:

```
2: eth0
    inet 192.168.1.100/24

3: wlan0
    inet 192.168.1.50/24

1: lo
    inet 127.0.0.1/8
```

---

# 📖 Understanding `ip a`

Example:

```
2: wlan0:
```

Interface name.

---

```
inet
```

IPv4 address.

---

```
inet6
```

IPv6 address.

---

```
link/ether
```

MAC Address.

---

```
UP
```

Interface is active.

---

```
DOWN
```

Interface is disabled.

---

# 🚦 Routing

Routing determines **where packets should travel**.

Linux stores this information in a routing table.

View it:

```bash
ip route
```

Example:

```
default via 192.168.1.1 dev wlan0
```

Meaning:

- Default route
- Gateway: 192.168.1.1
- Interface: wlan0

---

# 🚪 Default Gateway

The **Default Gateway** is usually your router.

When Linux doesn't know where to send traffic, it forwards it to the gateway.

Think of it as the **main exit gate** from your local network.

```
Laptop

↓

Router (Gateway)

↓

Internet

↓

Website
```

---

# 🏗 Basic Network Architecture

```
               Internet
                   │
             ISP Modem
                   │
                Router
          ┌────────┼────────┐
          │        │        │
      Laptop    Phone    Desktop
```

Every device receives its own IP address from the router.

---

# 🌐 DNS Basics

DNS stands for:

**Domain Name System**

Humans remember:

```
google.com
```

Computers communicate using:

```
142.250.x.x
```

DNS translates domain names into IP addresses.

Think of DNS as the **Internet's phonebook**.

---

# 🔄 DNS Resolution Process

```
User types:

google.com

        │

        ▼

DNS Server

        │

        ▼

Returns

142.250.x.x

        │

        ▼

Browser connects to the server
```

Without DNS, users would have to memorize IP addresses for every website.

---

# 🔒 Cybersecurity Perspective

Networking knowledge is essential for cybersecurity because attackers and defenders both rely on it.

Professionals use networking concepts to:

- Scan networks
- Discover devices
- Identify services
- Detect suspicious traffic
- Troubleshoot connectivity issues
- Investigate incidents
- Perform reconnaissance
- Monitor network communications

Understanding networking fundamentals is the first step before learning tools like:

- Nmap
- Wireshark
- Burp Suite
- Metasploit
- TCPDump

---

# 💡 Best Practices

✅ Learn both IPv4 and IPv6.

✅ Understand the difference between public and private IP addresses.

✅ Remember that `127.0.0.1` always refers to your own computer.

✅ Learn the `ip` command instead of relying on the older `ifconfig`.

✅ Always verify your network configuration before troubleshooting applications.

---

---

# 📡 Testing Network Connectivity

One of the first things a Linux administrator or cybersecurity professional checks is whether a system can communicate with another device.

The most common command is:

```bash
ping google.com
```

Example Output:

```
64 bytes from 142.250.xxx.xxx:
icmp_seq=1 ttl=117 time=18.5 ms
```

Stop ping by pressing:

```
Ctrl + C
```

---

# 🎯 What Does `ping` Do?

`ping` sends **ICMP Echo Request** packets to another host.

If the host replies, it sends back an **ICMP Echo Reply**.

This helps determine:

- Is the host online?
- Is the network working?
- How long does communication take?
- Is there packet loss?

---

# 📦 ICMP

ICMP stands for:

**Internet Control Message Protocol**

It is mainly used for:

- Diagnostics
- Error reporting
- Connectivity testing

Unlike TCP and UDP, ICMP does **not** transport application data.

---

# ⏱ Ping Only a Few Times

Instead of running forever:

```bash
ping -c 4 google.com
```

This sends exactly **4 packets**.

---

# 📊 Understanding Ping Output

Example:

```
64 bytes from 142.250.xxx.xxx

icmp_seq=1

ttl=117

time=18.2 ms
```

Meaning:

| Field | Description |
|---------|-------------|
| bytes | Packet size |
| icmp_seq | Packet number |
| ttl | Time To Live |
| time | Response time |

---

# 📈 Ping Statistics

Example:

```
4 packets transmitted

4 received

0% packet loss
```

Good network:

```
0% packet loss
```

Poor network:

```
25% packet loss

50% packet loss
```

High packet loss usually indicates network problems.

---

# 🌍 Downloading Files

## wget

`wget` downloads files directly from the internet.

Example:

```bash
wget https://example.com/file.txt
```

Useful for downloading:

- Wordlists
- Tools
- Scripts
- Software
- Updates

Downloaded files are saved in the current directory.

---

# 🌐 curl

Unlike `wget`, `curl` is designed to transfer data.

Example:

```bash
curl https://example.com
```

Instead of downloading the webpage, it displays the HTML source.

---

# 📑 View HTTP Headers

```bash
curl -I https://example.com
```

Example:

```
HTTP/1.1 200 OK

Server: nginx

Content-Type: text/html
```

Security professionals often inspect headers to identify:

- Web server software
- Response codes
- Security headers

---

# 🔌 Viewing Open Ports

Linux provides several tools to inspect network connections.

The modern command is:

```bash
ss -tuln
```

---

# 📖 Understanding `ss`

Options:

| Option | Meaning |
|---------|----------|
| -t | TCP |
| -u | UDP |
| -l | Listening Ports |
| -n | Numeric Output |

---

Example:

```
LISTEN

22

80

443
```

Meaning:

| Port | Service |
|--------|----------|
| 22 | SSH |
| 80 | HTTP |
| 443 | HTTPS |

---

# 🌐 Why Open Ports Matter

Every network service listens on a port.

Examples:

```
SSH

↓

22
```

```
HTTP

↓

80
```

```
HTTPS

↓

443
```

Attackers often scan ports to discover running services.

Defenders monitor ports to detect unauthorized services.

---

# 📜 netstat (Legacy Command)

Older Linux systems use:

```bash
netstat -tuln
```

Although still useful, **ss** is recommended because it is:

- Faster
- More efficient
- Included in modern Linux distributions

---

# 🔍 DNS Lookup Commands

## dig

```bash
dig google.com
```

Displays:

- IP Address
- DNS Server
- Query Time
- Record Type

---

## nslookup

```bash
nslookup google.com
```

Provides a simpler DNS lookup.

Both commands are useful when troubleshooting DNS issues.

---

# 🖥 Network Troubleshooting Workflow

When a website is unreachable:

```
Check Interface

↓

Check IP Address

↓

Check Gateway

↓

Ping Gateway

↓

Ping Internet

↓

Check DNS

↓

Inspect Open Connections

↓

Problem Identified
```

---

# 🌍 Real-World Cybersecurity Example

A penetration tester arrives at a client site.

The first steps might be:

```bash
ip a
```

Identify interfaces.

---

```bash
ip route
```

Identify gateway.

---

```bash
ping 8.8.8.8
```

Verify internet connectivity.

---

```bash
dig target.com
```

Resolve target IP.

---

```bash
ss -tuln
```

Check local listening services.

Networking commands are used before launching advanced security tools.

---

# 🛡 Cybersecurity Perspective

Attackers use networking to:

- Discover hosts
- Scan ports
- Enumerate services
- Identify operating systems
- Find exposed applications

Defenders use networking to:

- Detect intrusions
- Monitor traffic
- Investigate incidents
- Verify configurations
- Secure exposed services

Networking knowledge forms the foundation of:

- Ethical Hacking
- Penetration Testing
- Digital Forensics
- Incident Response
- SOC Analysis

---

# ⚠ Common Beginner Mistakes

❌ Confusing MAC addresses with IP addresses.

❌ Thinking `127.0.0.1` is the Internet IP.

❌ Using `ifconfig` without learning `ip`.

❌ Assuming a failed `ping` always means a host is offline.

❌ Forgetting that firewalls may block ICMP traffic.

---

# 🧪 Hands-on Lab

Run the following commands:

```bash
hostname
```

```bash
hostnamectl
```

```bash
ip a
```

```bash
ip route
```

```bash
ping -c 4 google.com
```

```bash
curl -I https://example.com
```

```bash
ss -tuln
```

```bash
dig google.com
```

If `dig` is unavailable:

```bash
nslookup google.com
```

---

# 🎯 Mini Challenge

1.

Find your hostname.

2.

Find your IP address.

3.

Find your MAC address.

4.

Find your default gateway.

5.

Ping Google four times.

6.

Retrieve only HTTP headers from:

```
https://example.com
```

7.

Display all listening TCP/UDP ports.

8.

Resolve the IP address of:

```
openai.com
```

---

# 📋 Networking Cheat Sheet

| Command | Purpose |
|----------|----------|
| `hostname` | Display hostname |
| `hostnamectl` | Detailed hostname information |
| `ip a` | Show interfaces and IP addresses |
| `ip route` | Show routing table |
| `ping host` | Test connectivity |
| `ping -c 4 host` | Send four packets |
| `ss -tuln` | Show listening ports |
| `netstat -tuln` | Legacy port viewer |
| `curl URL` | Retrieve webpage |
| `curl -I URL` | View HTTP headers |
| `wget URL` | Download file |
| `dig domain` | DNS lookup |
| `nslookup domain` | DNS lookup |

---

# 🧠 Memory Trick

```
ip

↓

Who am I on the network?
```

↓

```
ping

↓

Can I reach it?
```

↓

```
dig

↓

Where is it?
```

↓

```
curl

↓

What does it return?
```

↓

```
ss

↓

What is my computer listening on?
```

↓

```
wget

↓

Download it.
```

---

# ❓ Interview Questions

1. What is a network interface?

2. What is the difference between an IP address and a MAC address?

3. What is the purpose of the `ip` command?

4. What is a default gateway?

5. What is DNS?

6. What does `ping` use to test connectivity?

7. What is the difference between `curl` and `wget`?

8. Why is `ss` preferred over `netstat`?

9. What is the purpose of `dig`?

10. Why is networking knowledge important in cybersecurity?

---

# 🎯 Key Takeaways

✅ Networks allow devices to communicate.

✅ IP addresses identify devices on a network.

✅ MAC addresses identify network hardware.

✅ DNS translates domain names into IP addresses.

✅ `ip` is the modern Linux networking utility.

✅ `ping` tests connectivity using ICMP.

✅ `curl` retrieves web content.

✅ `wget` downloads files.

✅ `ss` displays listening ports.

✅ Networking fundamentals are essential before learning tools like Nmap and Wireshark.

---

# 📚 Next Lesson

➡ **09 - Bash Shell & Scripting Fundamentals**

Topics include:

- What is Bash?
- Shell Environment
- Variables
- User Input
- Conditional Statements (`if`)
- Loops (`for`, `while`)
- Functions
- Command-Line Arguments
- Command Chaining (`&&`, `||`, `;`)
- Writing Your First Bash Script

---

<div align="center">

## ⭐ "Cybersecurity begins with understanding how computers communicate before learning how to secure them."

**Happy Learning! 🐧**

</div>
