# 🌐 Linux Networking Fundamentals

> "Networking is the backbone of cybersecurity. Before learning tools like Nmap, Wireshark, Burp Suite, or Metasploit, you must understand how Linux communicates over a network."

---

# 📚 Table of Contents

1. What is a Network?
2. Network Interfaces
3. IP Addresses
4. MAC Addresses
5. Hostname
6. The `ip` Command
7. Routing & Default Gateway
8. Testing Connectivity with `ping`
9. Viewing Network Connections (`ss`)
10. `netstat` (Legacy Command)
11. Downloading Files (`wget`)
12. Accessing Web Resources (`curl`)
13. DNS Basics
14. DNS Lookup Commands
15. Common Networking Commands
16. Real-World Cybersecurity Use Cases
17. Best Practices
18. Key Takeaways
19. Practice Questions

---

# 🌍 What is a Network?

A **network** is a group of two or more devices connected together to exchange information.

Examples:

- 💻 Laptop ↔ Router
- 📱 Phone ↔ Wi-Fi
- 🖥️ Computer ↔ Server
- 🌐 Internet (a network of networks)

Without networking, computers cannot communicate with each other.

---

# 🔌 Network Interfaces

A **Network Interface** is the hardware or virtual connection through which a computer sends and receives network traffic.

Examples:

- Ethernet Adapter
- Wi-Fi Adapter
- Virtual Machine Adapter
- VPN Interface
- Loopback Interface

Think of a network interface as a **door**. Every piece of network traffic enters or leaves through one of these doors.

---

# 🌐 IP Address

An **IP Address (Internet Protocol Address)** uniquely identifies a device on a network.

Example:

```
192.168.1.100
```

Think of it as your **home address**.

Without an IP address, other devices wouldn't know where to send data.

## Types of IP Addresses

### Private IP

Used inside local networks.

Examples:

```
192.168.x.x
10.x.x.x
172.16.x.x – 172.31.x.x
```

### Public IP

Assigned by your Internet Service Provider (ISP).

Used to communicate over the Internet.

---

# 🏷️ MAC Address

Every network card has a unique **MAC (Media Access Control) Address**.

Example:

```
00:1A:2B:3C:4D:5E
```

Think of it as your network card's **serial number**.

Unlike an IP address, a MAC address is usually fixed to the hardware.

---

# ⚖️ IP Address vs MAC Address

| IP Address | MAC Address |
|------------|-------------|
| Logical Address | Physical Address |
| Can change | Usually permanent |
| Used for routing | Identifies network hardware |
| Assigned by network | Assigned by manufacturer |

---

# 🖥️ Hostname

A **Hostname** is the name given to a computer.

Example:

```
kali
```

Instead of remembering an IP address, users often recognize systems by their hostname.

View hostname:

```bash
hostname
```

---

# 📡 The `ip` Command

The modern networking command in Linux is:

```bash
ip a
```

or

```bash
ip addr
```

Example output:

```
2: eth0
    inet 192.168.1.100/24

3: wlan0
    inet 192.168.1.50/24

1: lo
    inet 127.0.0.1/8
```

---

# Common Interfaces

## Loopback

```
lo
```

Loopback address:

```
127.0.0.1
```

This allows your computer to communicate with itself.

---

## Ethernet

```
eth0
```

Represents a wired connection.

---

## Wireless

```
wlan0
```

Represents a Wi-Fi connection.

Modern Linux systems may use names like:

```
enp0s3
wlp2s0
```

---

# 🚦 Routing

A **Route** tells Linux where to send network traffic.

View routing table:

```bash
ip route
```

Example:

```
default via 192.168.1.1 dev wlan0
```

---

# 🚪 Default Gateway

The **Default Gateway** is usually your router.

When Linux doesn't know where to send traffic, it forwards it to the default gateway.

Think of the gateway as the **main exit** from your local network to the Internet.

---

# 📶 Testing Connectivity

## ping

Used to test whether another host is reachable.

```bash
ping google.com
```

Stop:

```
Ctrl + C
```

Send only four packets:

```bash
ping -c 4 google.com
```

### What ping tells you

- Internet connectivity
- DNS resolution
- Network latency
- Packet loss

---

# 📊 Viewing Network Connections

## ss

Modern Linux uses:

```bash
ss -tuln
```

Options:

| Option | Meaning |
|---------|----------|
| -t | TCP |
| -u | UDP |
| -l | Listening Ports |
| -n | Numeric Output |

Example:

```
LISTEN
22
80
443
```

Meaning:

- Port 22 → SSH
- Port 80 → HTTP
- Port 443 → HTTPS

---

# 📜 netstat (Legacy)

Older systems may still use:

```bash
netstat -tuln
```

Today, **ss** is the preferred command because it is faster and more efficient.

---

# 🌍 Downloading Files

## wget

Downloads files from the Internet.

Example:

```bash
wget https://example.com/file.txt
```

Useful for:

- Tools
- Wordlists
- Scripts
- Software packages

---

# 🌐 Accessing Web Resources

## curl

Displays data from a URL.

```bash
curl https://example.com
```

Shows the webpage source.

View only HTTP headers:

```bash
curl -I https://example.com
```

Example:

```
HTTP/1.1 200 OK
Server: nginx
Content-Type: text/html
```

---

# 📖 DNS (Domain Name System)

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

# 🔍 DNS Lookup

## dig

```bash
dig google.com
```

## nslookup

```bash
nslookup google.com
```

Both commands display DNS information such as IP addresses.

---

# 🛠️ Common Networking Commands

| Command | Purpose |
|----------|----------|
| hostname | Show system hostname |
| ip a | Show network interfaces |
| ip route | Show routing table |
| ping | Test connectivity |
| ping -c 4 | Send four packets |
| ss -tuln | View listening ports |
| netstat -tuln | Legacy alternative |
| curl | Access web resources |
| curl -I | View HTTP headers |
| wget | Download files |
| dig | DNS lookup |
| nslookup | DNS lookup |

---

# 🔒 Cybersecurity Importance

Networking is one of the most important topics in cybersecurity.

Security professionals use these commands to:

- Verify Internet connectivity
- Troubleshoot DNS problems
- Check listening services
- Download security tools
- Investigate suspicious connections
- Verify web servers
- Identify network configuration issues

Examples:

```bash
ping target.com
```

Check connectivity.

```bash
ss -tuln
```

View open/listening ports.

```bash
curl -I https://example.com
```

Check web server response.

```bash
dig google.com
```

Investigate DNS records.

---

# 💡 Best Practices

✅ Use `ip` instead of `ifconfig` on modern Linux systems.

✅ Prefer `ss` over `netstat`.

✅ Verify Internet connectivity before troubleshooting applications.

✅ Understand the difference between public and private IP addresses.

✅ Remember that `127.0.0.1` always refers to your own computer.

---

# 📝 Key Takeaways

- A network connects devices so they can communicate.
- A network interface is the connection point for network traffic.
- An IP address identifies a device on a network.
- A MAC address uniquely identifies network hardware.
- DNS translates domain names into IP addresses.
- `ping` tests connectivity.
- `ip a` displays network configuration.
- `ip route` displays routing information.
- `ss` displays listening ports.
- `curl` accesses web content.
- `wget` downloads files.

---

# ❓ Practice Questions

1. What is a network?
2. What is the purpose of a network interface?
3. What is the difference between an IP address and a MAC address?
4. What is the loopback address?
5. What does `ip a` display?
6. What is a default gateway?
7. What does `ping` do?
8. What is the difference between `curl` and `wget`?
9. What is DNS?
10. Why is `ss` preferred over `netstat` on modern Linux?
11. Which command displays the routing table?
12. Which command displays HTTP headers only?

---

> **Next Module:** Bash Scripting Fundamentals 🚀
