<div align="center">

# 🐉 Kali Linux Masterclass
## 📘 Phase 1 – Linux Fundamentals

# 11 - Linux Command Cheat Sheet & Productivity Tips

*"Professionals don't memorize thousands of commands—they know the right commands and how to use them efficiently."*

![Linux](https://img.shields.io/badge/Linux-Command%20Cheat%20Sheet-FCC624?style=for-the-badge&logo=linux)
![Kali](https://img.shields.io/badge/Kali-Linux-557C94?style=for-the-badge&logo=kalilinux)
![Productivity](https://img.shields.io/badge/Productivity-Pro-blue?style=for-the-badge)

</div>

---

# 📚 Table of Contents

- Introduction
- Terminal Navigation
- File & Directory Commands
- Viewing Files
- Searching
- Text Processing
- Permissions
- Users & Groups
- Processes
- Package Management
- Networking
- System Information
- Bash Productivity
- Input & Output Redirection
- Keyboard Shortcuts
- Cybersecurity Commands
- Daily Workflow
- Interview Tips
- Command Cheat Sheet
- Key Takeaways

---

# 🌟 Introduction

Linux has **thousands of commands**, but most professionals use the same **50–100 commands** every day.

This guide brings together the most useful commands you've learned in **Phase 1** into a single quick-reference document.

---

# 📂 Navigation Commands

| Command | Description |
|----------|-------------|
| `pwd` | Show current directory |
| `ls` | List files |
| `ls -l` | Long listing |
| `ls -la` | Show hidden files |
| `ls -lh` | Human-readable sizes |
| `ls -R` | List recursively |
| `cd folder` | Change directory |
| `cd ..` | Go back one directory |
| `cd ~` | Go to home directory |
| `tree` | Display directory tree |

---

# 📁 File Management

| Command | Description |
|----------|-------------|
| `touch file.txt` | Create file |
| `mkdir folder` | Create directory |
| `mkdir -p` | Create nested directories |
| `cp file backup` | Copy file |
| `cp -r folder backup` | Copy directory |
| `mv old new` | Move or rename |
| `rm file` | Delete file |
| `rm -r folder` | Delete directory |
| `rm -rf folder` | Force delete recursively *(use carefully)* |
| `find . -name "*.txt"` | Search files |

---

# 📖 Viewing File Contents

| Command | Description |
|----------|-------------|
| `cat file` | Display file |
| `less file` | Scroll through file |
| `more file` | View page by page |
| `head file` | First 10 lines |
| `head -20 file` | First 20 lines |
| `tail file` | Last 10 lines |
| `tail -f log.txt` | Follow log updates |
| `nl file` | Show line numbers |

---

# 🔍 Searching & Text Processing

| Command | Description |
|----------|-------------|
| `grep word file` | Search text |
| `grep -i` | Ignore case |
| `grep -r word dir` | Recursive search |
| `sort file` | Sort lines |
| `uniq file` | Remove duplicates |
| `wc file` | Count lines, words, bytes |
| `cut` | Extract columns |
| `tr` | Replace characters |
| `sed` | Stream editor |
| `awk` | Advanced text processing |

---

# 🔐 Permissions

| Command | Description |
|----------|-------------|
| `chmod 755 file` | Change permissions |
| `chmod +x script.sh` | Make executable |
| `chown user file` | Change owner |
| `chgrp group file` | Change group |
| `ls -l` | View permissions |

---

# 👥 Users & Groups

| Command | Description |
|----------|-------------|
| `whoami` | Current user |
| `id` | User information |
| `groups` | Show groups |
| `who` | Logged-in users |
| `sudo` | Run as administrator |
| `useradd` | Create user |
| `usermod` | Modify user |
| `userdel` | Delete user |
| `passwd` | Change password |
| `groupadd` | Create group |

---

# ⚙ Processes & Services

| Command | Description |
|----------|-------------|
| `ps` | Running processes |
| `ps aux` | Detailed process list |
| `top` | Live process monitor |
| `htop` | Interactive process monitor |
| `kill PID` | Stop process |
| `kill -9 PID` | Force stop |
| `killall name` | Kill by name |
| `jobs` | Background jobs |
| `fg` | Foreground job |
| `bg` | Background job |
| `systemctl status` | Service status |

---

# 📦 Package Management

| Command | Description |
|----------|-------------|
| `apt update` | Refresh package list |
| `apt upgrade` | Upgrade software |
| `apt install` | Install package |
| `apt remove` | Remove package |
| `apt purge` | Remove package & config |
| `apt autoremove` | Remove unused packages |
| `apt search` | Search packages |
| `apt show` | Package details |
| `dpkg -l` | List installed packages |

---

# 🌐 Networking

| Command | Description |
|----------|-------------|
| `ip a` | Show IP addresses |
| `ip route` | Routing table |
| `ping google.com` | Test connectivity |
| `hostname` | Show hostname |
| `ss -tuln` | Show listening ports |
| `curl URL` | Download webpage |
| `wget URL` | Download file |
| `nslookup domain.com` | DNS lookup |
| `dig domain.com` | Detailed DNS lookup |
| `traceroute host` | Trace network path |

---

# 💻 System Information

| Command | Description |
|----------|-------------|
| `uname -a` | Kernel information |
| `hostnamectl` | System details |
| `uptime` | System uptime |
| `date` | Current date |
| `cal` | Calendar |
| `free -h` | RAM usage |
| `df -h` | Disk usage |
| `du -sh folder` | Folder size |
| `lscpu` | CPU information |
| `lsblk` | Storage devices |

---

# 🐚 Bash Productivity

| Command | Description |
|----------|-------------|
| `history` | Command history |
| `!!` | Repeat last command |
| `!25` | Run command #25 |
| `!apt` | Last command starting with apt |
| `alias ll='ls -la'` | Create shortcut |
| `unalias ll` | Remove alias |
| `echo $PATH` | View PATH |
| `printenv` | Environment variables |
| `source ~/.bashrc` | Reload Bash config |

---

# 🔄 Redirection

## Output

```bash
ls > files.txt
```

Overwrite file.

---

## Append

```bash
echo "Hello" >> notes.txt
```

---

## Input

```bash
sort < names.txt
```

---

## Error

```bash
ls missing.txt 2> errors.txt
```

---

## Output + Error

```bash
command > output.txt 2>&1
```

---

## Pipe

```bash
cat file.txt | grep Linux
```

---

# ⚡ Command Chaining

| Operator | Meaning |
|----------|----------|
| `;` | Run all commands |
| `&&` | Run next if success |
| `||` | Run next if failure |
| `|` | Pass output to next command |

Examples:

```bash
mkdir test && cd test
```

```bash
mkdir test || echo "Already exists"
```

```bash
pwd ; ls ; date
```

---

# ⌨ Keyboard Shortcuts

| Shortcut | Purpose |
|----------|----------|
| `Ctrl + C` | Stop current process |
| `Ctrl + Z` | Suspend process |
| `Ctrl + D` | Logout / End input |
| `Ctrl + L` | Clear screen |
| `Ctrl + A` | Beginning of line |
| `Ctrl + E` | End of line |
| `Ctrl + U` | Delete to line start |
| `Ctrl + K` | Delete to line end |
| `Ctrl + R` | Search command history |
| `Tab` | Auto-complete |

---

# 🛡 Cybersecurity Commands

| Command | Purpose |
|----------|----------|
| `whoami` | Current user |
| `id` | User privileges |
| `sudo -l` | Allowed sudo commands |
| `find / -perm -4000 2>/dev/null` | Find SUID files |
| `ss -tuln` | Open ports |
| `ps aux` | Running processes |
| `top` | Resource monitoring |
| `cat /etc/passwd` | User accounts |
| `cat /etc/shadow` | Password hashes *(root only)* |
| `journalctl` | View system logs |

> ⚠️ Some commands require root privileges.

---

# 🚀 Daily Linux Workflow

```text
Open Terminal
      │
      ▼
pwd
      │
      ▼
ls
      │
      ▼
Navigate
      │
      ▼
Create/Edit Files
      │
      ▼
Check Permissions
      │
      ▼
Run Programs
      │
      ▼
Monitor Processes
      │
      ▼
Update Packages
      │
      ▼
Logout
```

---

# 💼 Productivity Tips

## ✔ Use TAB Completion

Instead of typing long filenames, press **Tab**.

---

## ✔ Use History

```bash
history
```

or

```bash
Ctrl + R
```

to search previous commands.

---

## ✔ Create Aliases

Example:

```bash
alias update='sudo apt update && sudo apt upgrade'
```

---

## ✔ Learn Pipes

Instead of:

```bash
cat file.txt
```

Use:

```bash
cat file.txt | grep password
```

---

## ✔ Read the Manual

Every command has documentation.

```bash
man command
```

Example:

```bash
man grep
```

---

## ✔ Use `--help`

Quick help:

```bash
grep --help
```

---

# 🎯 Mini Challenge

Without looking at previous notes:

✔ Find your IP address.

✔ Display memory usage.

✔ Show running processes.

✔ Create a directory.

✔ Make a script executable.

✔ Search for all `.log` files.

✔ View disk usage.

✔ Search command history.

---

# 🧠 Memory Map

```
Navigation

↓

Files

↓

Permissions

↓

Users

↓

Processes

↓

Networking

↓

Packages

↓

Automation

↓

Cybersecurity
```

---

# ❓ Interview Questions

1. Which command displays the current directory?

2. Difference between `cp` and `mv`?

3. Difference between `>` and `>>`?

4. Difference between `&&` and `;`?

5. What does `chmod +x` do?

6. Which command displays processes?

7. What does `sudo` do?

8. Difference between `apt update` and `apt upgrade`?

9. What does `Ctrl + C` do?

10. Why is `history` useful?

---

# 📋 Ultimate Quick Reference

| Category | Most Important Commands |
|-----------|-------------------------|
| Navigation | `pwd`, `ls`, `cd` |
| Files | `cp`, `mv`, `rm`, `mkdir`, `touch` |
| Viewing | `cat`, `less`, `head`, `tail` |
| Search | `find`, `grep` |
| Permissions | `chmod`, `chown` |
| Users | `whoami`, `id`, `sudo` |
| Processes | `ps`, `top`, `kill` |
| Networking | `ip`, `ping`, `ss`, `curl` |
| Packages | `apt`, `dpkg` |
| Bash | `history`, `alias`, `printenv` |

---

# 🎯 Key Takeaways

✅ You now know the commands used most frequently by Linux administrators and cybersecurity professionals.

✅ Keyboard shortcuts and command chaining can greatly improve productivity.

✅ Using `man` and `--help` helps you learn commands independently.

✅ Mastering these commands provides a strong foundation for ethical hacking, system administration, and scripting.

---

# 📚 Next Lesson

➡ **12 - Phase 1 Final Revision**

Topics include:

- Complete Linux Fundamentals Mind Map
- Summary Tables
- Frequently Asked Interview Questions
- Practical Exercises
- Common Mistakes
- Linux Command Revision
- Phase 1 Challenge
- Cybersecurity Review
- Final Notes Before Phase 2

---

<div align="center">

## ⭐ "A Linux expert isn't someone who knows every command—it's someone who knows where to find the right one and how to use it effectively."

# 🏆 Congratulations!

You have now completed the **Linux learning content** of Phase 1.

Only one final document remains:

**📖 Phase 1 Final Revision**

After that, you'll have a complete Linux fundamentals handbook ready for your cybersecurity journey.

**Happy Learning! 🐧**

</div>
