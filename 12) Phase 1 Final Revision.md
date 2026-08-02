<div align="center">

# 🐉 Kali Linux Masterclass
# 📘 Phase 1 – Final Revision

# 🏆 Linux Fundamentals Revision Handbook

*"Knowledge is gained by learning. Mastery is gained by revision and practice."*

![Linux](https://img.shields.io/badge/Linux-Fundamentals-FCC624?style=for-the-badge&logo=linux)
![Kali](https://img.shields.io/badge/Kali-Linux-557C94?style=for-the-badge&logo=kalilinux)
![Cybersecurity](https://img.shields.io/badge/Cyber-Security-red?style=for-the-badge)
![Revision](https://img.shields.io/badge/Revision-Final-success?style=for-the-badge)

# 🎉 Congratulations!

**You have completed Phase 1 of your Kali Linux Journey!**

</div>

---

# 📚 Phase 1 Topics Covered

✅ 01 - Introduction to Kali Linux

✅ 02 - Linux Terminal & File System

✅ 03 - Working with Files & Text

✅ 04 - Linux Permissions

✅ 05 - Users & Groups

✅ 06 - Processes & Services

✅ 07 - Package Management

✅ 08 - Bash Basics

✅ 09 - Environment Variables

✅ 10 - Linux File System Deep Dive

✅ 11 - Command Cheat Sheet & Productivity Tips

---

# 🧠 Complete Linux Mind Map

```text
                     Linux
                        │
        ┌───────────────┼────────────────┐
        │               │                │
     Terminal        File System      Security
        │               │                │
        │               │                │
 Navigation        Files & Dirs     Permissions
        │               │                │
        │               │                │
 Bash          Hard Links       Users & Groups
        │               │                │
 Environment     Soft Links      sudo
 Variables          Inodes            │
        │               │        Processes
        │               │             │
 Package Manager    /proc         Services
        │               │             │
        └───────────────┼─────────────┘
                        │
                  Cybersecurity
```

---

# 🐧 Linux Directory Structure

```text
/

├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

### Important Directories

| Directory | Purpose |
|------------|----------|
| `/home` | User files |
| `/root` | Root user's home |
| `/etc` | Configuration files |
| `/var` | Logs and variable data |
| `/tmp` | Temporary files |
| `/proc` | Process information |
| `/sys` | Hardware and kernel information |
| `/dev` | Device files |
| `/usr` | Applications and libraries |
| `/bin` | Essential commands |

---

# 💻 Essential Linux Commands

## Navigation

```bash
pwd
ls
ls -la
cd
tree
```

---

## File Management

```bash
touch
mkdir
cp
mv
rm
find
```

---

## Viewing Files

```bash
cat
less
head
tail
nl
```

---

## Searching

```bash
grep
sort
uniq
wc
```

---

## Permissions

```bash
chmod
chown
chgrp
```

---

## Users

```bash
whoami
id
groups
passwd
sudo
```

---

## Processes

```bash
ps
top
htop
kill
jobs
systemctl
```

---

## Packages

```bash
apt update
apt upgrade
apt install
apt remove
```

---

## Networking

```bash
ip a
ping
ss
curl
wget
```

---

# 🔐 Linux Permissions Summary

```text
r = Read = 4

w = Write = 2

x = Execute = 1
```

Example

```
755

↓

Owner

7

↓

rwx

Group

5

↓

r-x

Others

5

↓

r-x
```

---

# 👥 User Types

```text
Root

↓

UID 0

↓

Full Control
```

```
Regular User

↓

Limited Permissions
```

```
System User

↓

Runs Services
```

---

# ⚙ Process Lifecycle

```text
Program

↓

Loaded

↓

Running

↓

Waiting

↓

Finished

↓

Terminated
```

---

# 📦 Package Management Workflow

```text
sudo apt update

↓

Download Latest Package Lists

↓

sudo apt upgrade

↓

Install Updates

↓

sudo apt install package

↓

Software Ready
```

---

# 🐚 Bash Quick Revision

## Variables

```bash
name="Farhan"

echo $name
```

---

## Alias

```bash
alias ll='ls -la'
```

---

## Command Chaining

```bash
command1 ; command2

command1 && command2

command1 || command2
```

---

## Wildcards

```text
*

Matches Everything
```

```text
?

One Character
```

```text
[]

Character Range
```

---

# 🌍 Environment Variables

Most Common

```bash
HOME

USER

PWD

PATH

SHELL
```

View

```bash
printenv
```

Create

```bash
export TEST="Linux"
```

Reload

```bash
source ~/.bashrc
```

---

# 📂 Hard Link vs Symbolic Link

| Hard Link | Symbolic Link |
|------------|---------------|
| Same inode | Different inode |
| Same data | Points to path |
| Doesn't break if original name is removed (as long as another hard link exists) | Breaks if target removed |
| Cannot cross file systems | Can cross file systems |

---

# 💾 File Descriptors

| Number | Name |
|----------|------|
| 0 | stdin |
| 1 | stdout |
| 2 | stderr |

Example

```bash
ls > output.txt

ls missing.txt 2> errors.txt
```

---

# 📋 Frequently Used Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| Ctrl + C | Stop process |
| Ctrl + Z | Suspend process |
| Ctrl + D | Logout |
| Ctrl + L | Clear screen |
| Ctrl + A | Beginning of line |
| Ctrl + E | End of line |
| Ctrl + R | Search history |
| Tab | Auto-complete |

---

# 🛡 Linux Security Principles

✔ Least Privilege

✔ Strong Passwords

✔ Regular Updates

✔ Use sudo Instead of Root

✔ Verify Downloads

✔ Restrict File Permissions

✔ Monitor Logs

✔ Remove Unused Software

✔ Backup Important Data

---

# 🎯 Common Beginner Mistakes

❌ Using `rm -rf` carelessly.

❌ Logging in as root for everyday tasks.

❌ Forgetting `sudo`.

❌ Ignoring updates.

❌ Setting incorrect file permissions.

❌ Forgetting to make scripts executable.

❌ Editing system files without backups.

❌ Overwriting the `PATH` variable.

---

# 🔥 25 Essential Commands to Memorize

```text
pwd
ls
cd
touch
mkdir
cp
mv
rm
find
cat
grep
chmod
chown
whoami
id
ps
top
kill
systemctl
apt
history
echo
alias
printenv
man
```

---

# 🧪 Final Practical Challenge

Complete these tasks without looking at your notes.

### 📁 File Management

- Create a directory named `Practice`
- Create three text files
- Copy one file
- Rename another
- Delete one file

---

### 🔐 Permissions

- Make a Bash script executable.
- Change its owner (if applicable).
- View its permissions.

---

### 👤 Users

- Display your UID.
- List your groups.
- Show your username.

---

### ⚙ Processes

- Find your shell's PID.
- Start a background process:

```bash
sleep 300 &
```

- Display jobs.
- Stop the process.

---

### 📦 Packages

- Refresh package information.
- Search for `git`.
- Show package details.

---

### 🌐 Networking

- Show your IP address.
- Test internet connectivity.
- Display listening ports.

---

### 🐚 Bash

- Create an alias.
- Create a variable.
- Display an environment variable.
- Execute a previous command using history.

---

### 📂 File System

- View inode numbers.
- Create a symbolic link.
- Create a hard link.
- Display disk usage.

---

# 💼 Mini Interview

Answer these without Google.

1. What is Linux?

2. What is Bash?

3. What is an inode?

4. Difference between hard and symbolic links?

5. What is a daemon?

6. What is `sudo`?

7. Explain `PATH`.

8. Difference between shell and terminal?

9. What is a process?

10. What is `systemctl`?

11. Difference between `apt update` and `apt upgrade`?

12. What is `/proc`?

13. What is `/dev/null`?

14. Difference between `stdout` and `stderr`?

15. Why is Linux preferred for cybersecurity?

---

# 🏆 Phase 1 Achievement Checklist

| Skill | Status |
|---------|:------:|
| Linux Installation & Basics | ✅ |
| Terminal Navigation | ✅ |
| File Management | ✅ |
| Text Processing | ✅ |
| Permissions | ✅ |
| Users & Groups | ✅ |
| Processes & Services | ✅ |
| Package Management | ✅ |
| Bash Basics | ✅ |
| Environment Variables | ✅ |
| Linux Internals | ✅ |
| Productivity Tips | ✅ |

---

# 🚀 What's Next?

## Phase 2 – Linux for Cybersecurity

Now that you understand Linux fundamentals, you're ready to learn how attackers and defenders actually use Linux in cybersecurity.

### Topics You'll Learn

- 🔥 Advanced Bash Scripting
- 🌐 Networking Fundamentals
- 📡 TCP/IP Deep Dive
- 🔍 Packet Analysis
- 🛰 DNS & HTTP
- 🔒 SSH
- 🔥 Firewall Basics
- 📝 Log Analysis
- 📂 Cron Jobs
- ⚡ System Monitoring
- 🛠 Essential Linux Security Tools
- 🔎 Linux Enumeration
- 📊 Performance Monitoring

This is where Linux starts becoming a **professional cybersecurity operating system**, rather than just another OS.

---

# 🎖 Final Words

> **"A hacker isn't someone who memorizes commands. A hacker understands how systems work."**

You have now built a solid foundation in Linux fundamentals.

The real journey begins from here—using Linux to analyze, secure, automate, investigate, and test systems.

Keep practicing. Every command you type strengthens your skills.

---

<div align="center">

# 🏆 Congratulations!

## 🎉 Phase 1 Successfully Completed!

**Linux Fundamentals ✔**

**Ready for Phase 2 ✔**

### 🐧 Keep Learning • Keep Practicing • Keep Hacking (Ethically)

⭐ **Happy Learning!**

</div>
