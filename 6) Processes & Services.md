<div align="center">

# 🐉 Kali Linux Masterclass
## 📘 Phase 1 – Linux Fundamentals

# 06 - Linux Processes & Services

*"Every program you run becomes a process. Understanding processes means understanding how Linux actually works."*

![Linux](https://img.shields.io/badge/Linux-Processes%20%26%20Services-FCC624?style=for-the-badge&logo=linux)
![Kali](https://img.shields.io/badge/Kali-Linux-557C94?style=for-the-badge&logo=kalilinux)
![Cybersecurity](https://img.shields.io/badge/Cyber-Security-red?style=for-the-badge)

</div>

---

# 📚 Table of Contents

- Introduction
- What is a Process?
- Process Lifecycle
- Process States
- Foreground & Background Processes
- Process IDs (PID)
- Parent & Child Processes
- Viewing Processes
- Managing Processes
- Jobs
- Nice & Renice
- Services & Daemons
- systemctl
- Real-World Cybersecurity Example
- Hands-on Lab
- Cheat Sheet
- Interview Questions
- Key Takeaways

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

✅ Understand Linux processes

✅ View running processes

✅ Manage processes

✅ Control background jobs

✅ Manage Linux services

✅ Understand daemons and system services

---

# 🌟 Introduction

Whenever you open a program in Linux—

- Firefox
- Terminal
- Wireshark
- Burp Suite
- VS Code

Linux creates a **process**.

A process is simply a **running instance of a program**.

Without processes,

nothing on Linux can actually run.

---

# 🧠 Program vs Process

Many beginners confuse these terms.

| Program | Process |
|----------|----------|
| Stored on disk | Running in memory |
| Passive | Active |
| Executable file | Executing program |

Example

```
firefox

↓

Double Click

↓

Running Firefox

↓

Process
```

---

# ⚙ Process Lifecycle

```
Program

↓

Loaded into RAM

↓

Running

↓

Waiting

↓

Finished

↓

Terminated
```

Linux constantly creates and destroys processes.

---

# 📌 Process States

| State | Meaning |
|---------|----------|
| R | Running |
| S | Sleeping |
| D | Waiting for I/O |
| T | Stopped |
| Z | Zombie Process |

---

## Zombie Process

A zombie is a process that has finished execution but whose parent has not yet collected its exit status.

Zombie processes consume very little memory but may indicate poorly written software if many accumulate.

---

# 🆔 Process ID (PID)

Every process has a unique **Process ID (PID)**.

Example

```
Firefox

PID 3154
```

```
Terminal

PID 2287
```

Linux uses the PID to identify and manage processes.

---

# 👨‍👦 Parent & Child Processes

Every process (except the first one) is created by another process.

```
systemd (PID 1)

│

├── Terminal

│      │

│      ├── Bash

│             │

│             ├── nano

│             └── grep
```

This forms a process tree.

---

# 📋 ps

Displays information about running processes.

---

## View Current Terminal Processes

```bash
ps
```

---

## View All Processes

```bash
ps -e
```

or

```bash
ps -A
```

---

## Detailed Process List

```bash
ps -ef
```

or

```bash
ps aux
```

---

## Common Columns

| Column | Meaning |
|----------|---------|
| PID | Process ID |
| USER | Process Owner |
| %CPU | CPU Usage |
| %MEM | Memory Usage |
| COMMAND | Program Name |

---

# 📊 top

Displays real-time system activity.

```bash
top
```

Shows

- CPU usage
- Memory usage
- Running processes
- Load average

Press

```
q
```

to quit.

---

# 🚀 htop

An improved version of `top`.

```bash
htop
```

Features

✔ Colorful interface

✔ Easier navigation

✔ Interactive process management

✔ Better readability

> Note: `htop` may need to be installed first on some systems.

---

# ❌ kill

Terminates a process using its PID.

Example

```bash
kill 3154
```

Linux sends a termination signal to the process.

---

# 💀 kill -9

Forcefully terminates a process.

```bash
kill -9 3154
```

Use only when a process refuses to stop normally.

---

# 🎯 killall

Terminates processes by name.

```bash
killall firefox
```

Instead of specifying a PID,

use the process name.

---

# 🎛 Foreground Process

Runs directly inside the terminal.

Example

```bash
nano notes.txt
```

The terminal waits until the program finishes.

---

# 🌙 Background Process

Runs without occupying the terminal.

Example

```bash
firefox &
```

The ampersand (`&`) sends the process to the background.

---

# 📦 jobs

Displays background jobs started from the current shell.

```bash
jobs
```

Example

```
[1]+ Running firefox &
```

---

# ▶ fg

Brings a background job back to the foreground.

```bash
fg %1
```

---

# ◀ bg

Continues a stopped job in the background.

```bash
bg %1
```

---

# 🎚 nice

Controls process priority when starting a process.

```bash
nice -n 10 program
```

Higher nice value

↓

Lower priority

---

# 🔄 renice

Changes the priority of an existing process.

```bash
sudo renice 5 -p 3154
```

---

# ⚙ What is a Service?

A **service** is a program that runs in the background and provides functionality to the system.

Examples

- SSH Server
- Apache Web Server
- MySQL
- Docker
- NetworkManager

Most services start automatically during system boot.

---

# 👻 What is a Daemon?

A **daemon** is a background process that runs continuously without user interaction.

Examples

```
sshd

cron

systemd

cups

NetworkManager
```

Daemons often have names ending with **d** (daemon), although this is a convention rather than a rule.

---

# 🧩 systemd

Modern Linux systems use **systemd** to manage services and the boot process.

The first process started during boot is usually:

```
PID 1

↓

systemd
```

---

# ⚙ systemctl

Manage services using `systemctl`.

---

## Check Service Status

```bash
systemctl status ssh
```

---

## Start a Service

```bash
sudo systemctl start ssh
```

---

## Stop a Service

```bash
sudo systemctl stop ssh
```

---

## Restart a Service

```bash
sudo systemctl restart ssh
```

---

## Enable at Boot

```bash
sudo systemctl enable ssh
```

---

## Disable at Boot

```bash
sudo systemctl disable ssh
```

---

## List Running Services

```bash
systemctl list-units --type=service
```

---

# 🌍 Real-World Cybersecurity Example

A web server suddenly becomes slow.

The administrator investigates.

```bash
top
```

Finds a suspicious process consuming 95% CPU.

Checks more information.

```bash
ps aux
```

Terminates the malicious process.

```bash
kill PID
```

Verifies the web server service.

```bash
systemctl status apache2
```

This workflow is common during incident response.

---

# 🛡 Cybersecurity Perspective

Attackers often:

- Hide malicious processes
- Create persistent services
- Launch cryptocurrency miners
- Install backdoor daemons

Defenders monitor:

- Unknown processes
- Unexpected services
- High CPU usage
- High memory usage
- Suspicious parent-child process relationships

---

# ⚠ Common Beginner Mistakes

❌ Using `kill -9` immediately without trying a normal `kill`.

❌ Killing system processes accidentally.

❌ Running unnecessary services.

❌ Ignoring CPU and memory usage.

❌ Forgetting that services may restart automatically.

---

# 🧪 Hands-on Lab

```bash
ps

ps aux

top

jobs

sleep 120 &

jobs

fg %1

Ctrl + Z

bg %1

jobs

killall sleep

systemctl status ssh
```

If `ssh` is not installed, replace it with another available service such as `NetworkManager`.

---

# 🎯 Mini Challenge

1.

Find your current shell's PID.

```bash
echo $$
```

2.

List all running processes.

3.

Start a background process.

```bash
sleep 300 &
```

4.

Display background jobs.

5.

Terminate the process.

6.

Check the status of a system service.

7.

Identify the process using the most CPU with `top`.

---

# 📋 Command Cheat Sheet

| Command | Purpose |
|----------|----------|
| ps | Show processes |
| ps aux | Detailed process list |
| top | Real-time process monitor |
| htop | Interactive process monitor |
| kill PID | Stop process |
| kill -9 PID | Force stop process |
| killall NAME | Kill by process name |
| jobs | Show background jobs |
| fg | Foreground job |
| bg | Background job |
| nice | Start with custom priority |
| renice | Change process priority |
| systemctl status | Service status |
| systemctl start | Start service |
| systemctl stop | Stop service |
| systemctl restart | Restart service |
| systemctl enable | Start service at boot |
| systemctl disable | Disable service at boot |

---

# 🧠 Memory Trick

```
ps

Process Status
```

```
top

Top Resource Usage
```

```
kill

Stop by PID
```

```
killall

Stop by Name
```

```
jobs

Background Jobs
```

```
systemctl

System Control
```

---

# ❓ Interview Questions

1. What is a process?

2. What is the difference between a program and a process?

3. What is a PID?

4. What is a daemon?

5. What is a service?

6. Explain the difference between `kill` and `kill -9`.

7. What is the purpose of `systemctl`?

8. What is the difference between foreground and background processes?

9. What is a zombie process?

10. What does PID 1 usually represent on modern Linux systems?

---

# 🎯 Key Takeaways

✅ A process is a running instance of a program.

✅ Every process has a unique PID.

✅ `ps`, `top`, and `htop` help monitor processes.

✅ `kill` and `killall` terminate processes.

✅ Background jobs improve multitasking.

✅ Services provide system functionality in the background.

✅ `systemd` and `systemctl` manage services on most modern Linux systems.

✅ Understanding processes is essential for Linux administration, troubleshooting, and cybersecurity.

---

# 📚 Next Lesson

➡ **07 - Package Management**

Topics include:

- APT
- Repositories
- apt update
- apt upgrade
- apt install
- apt remove
- apt autoremove
- apt search
- dpkg
- Package Security
- Keeping Kali Updated

---

<div align="center">

## ⭐ "Every application is just a process. Learn to control processes, and you learn to control Linux."

**Happy Learning! 🐧**

</div>
````
