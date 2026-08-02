<div align="center">

# 🐉 Kali Linux Masterclass
## 📘 Phase 1 – Linux Fundamentals

# 07 - Package Management

*"Installing software is easy. Managing it securely is what makes a Linux professional."*

![Linux](https://img.shields.io/badge/Linux-Package%20Management-FCC624?style=for-the-badge&logo=linux)
![Kali](https://img.shields.io/badge/Kali-Linux-557C94?style=for-the-badge&logo=kalilinux)
![APT](https://img.shields.io/badge/APT-Debian-blue?style=for-the-badge)

</div>

---

# 📚 Table of Contents

- Introduction
- What is a Package?
- What is Package Management?
- Package Managers
- Repositories
- APT Architecture
- Updating vs Upgrading
- Installing Packages
- Removing Packages
- Searching Packages
- Package Information
- dpkg
- Repository Management
- Best Practices
- Cybersecurity Perspective
- Hands-on Lab
- Cheat Sheet
- Interview Questions
- Key Takeaways

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

✅ Understand Linux packages

✅ Install and remove software

✅ Update package information

✅ Upgrade installed software

✅ Search for packages

✅ Understand repositories and package security

---

# 🌟 Introduction

Unlike Windows, Linux software is usually **not downloaded from random websites**.

Instead, software is installed from **trusted repositories** maintained by the operating system.

This provides:

- Better security
- Easier updates
- Automatic dependency management
- Centralized software management

---

# 📦 What is a Package?

A **package** is a compressed file containing everything needed to install software.

It usually includes:

- Program files
- Libraries
- Configuration files
- Documentation
- Installation scripts

Example packages:

```
nmap

wireshark

curl

git

python3
```

---

# 🛠 What is Package Management?

Package management is the process of:

- Installing software
- Updating software
- Removing software
- Managing dependencies
- Verifying package integrity

Linux automates these tasks using package managers.

---

# 🧩 Package Managers

Different Linux distributions use different package managers.

| Distribution | Package Manager | Package Format |
|--------------|----------------|----------------|
| Debian / Kali / Ubuntu | APT | `.deb` |
| Fedora | DNF | `.rpm` |
| CentOS / RHEL | YUM / DNF | `.rpm` |
| Arch Linux | Pacman | `.pkg.tar.zst` |

In Kali Linux, **APT** is the primary package manager.

---

# 🌐 What is a Repository?

A **repository** is a trusted online server that stores software packages.

Instead of downloading software manually:

```
User

↓

APT

↓

Repository

↓

Package Download

↓

Installation
```

Repositories also contain updates and security patches.

---

# 🏗 APT Architecture

```
                User
                  │
                  ▼
             apt install
                  │
                  ▼
          Package Database
                  │
                  ▼
        Kali Repository Server
                  │
                  ▼
        Download Packages
                  │
                  ▼
        Install Dependencies
                  │
                  ▼
          Software Installed
```

APT handles dependency resolution automatically.

---

# 🔄 apt update

## What does it do?

Downloads the latest package lists from configured repositories.

```bash
sudo apt update
```

Think of it as refreshing a software catalog.

**Important:** `apt update` does **not** install updates.

---

# ⬆ apt upgrade

Installs newer versions of installed packages.

```bash
sudo apt upgrade
```

APT checks the updated package list and upgrades eligible packages.

---

# ⚡ Difference

| Command | Purpose |
|----------|----------|
| `apt update` | Refresh package information |
| `apt upgrade` | Install available updates |

A common workflow is:

```bash
sudo apt update

sudo apt upgrade
```

---

# 📥 apt install

Installs new software.

Example:

```bash
sudo apt install nmap
```

APT will:

1. Find the package.
2. Download it.
3. Resolve dependencies.
4. Install everything required.

---

## Install Multiple Packages

```bash
sudo apt install git curl wget
```

---

# 🗑 apt remove

Removes installed software but may leave configuration files.

```bash
sudo apt remove nmap
```

---

# 🧹 apt purge

Removes the package **and** its configuration files.

```bash
sudo apt purge nmap
```

Use this when you want a completely clean removal.

---

# 🧼 apt autoremove

Removes unused dependencies that are no longer needed.

```bash
sudo apt autoremove
```

This helps keep your system clean.

---

# 🔍 apt search

Search for available packages.

```bash
apt search wireshark
```

---

# 📖 apt show

Displays detailed information about a package.

```bash
apt show nmap
```

Information includes:

- Version
- Description
- Dependencies
- Maintainer
- Installed size

---

# 📋 apt list

List installed packages:

```bash
apt list --installed
```

List upgradable packages:

```bash
apt list --upgradable
```

---

# 📦 dpkg

`dpkg` is the low-level package management tool used by Debian-based systems.

APT actually uses `dpkg` behind the scenes.

---

## Install a Local Package

```bash
sudo dpkg -i package.deb
```

---

## List Installed Packages

```bash
dpkg -l
```

---

## Check Package Information

```bash
dpkg -s nmap
```

---

# 📁 Repository Configuration

APT reads repository information from:

```text
/etc/apt/sources.list
```

Additional repository files may be stored in:

```text
/etc/apt/sources.list.d/
```

Be cautious when adding third-party repositories.

---

# 🔒 Package Verification

Software from official repositories is digitally signed.

This helps ensure:

- Authenticity
- Integrity
- Protection against tampering

Always prefer official repositories over unknown sources.

---

# 🌍 Real-World Cybersecurity Example

A penetration tester needs a network scanning tool.

Instead of downloading an installer from an unknown website:

```bash
sudo apt update

sudo apt install nmap
```

The package comes from Kali's trusted repositories, reducing the risk of installing malicious software.

---

# 🛡 Cybersecurity Perspective

Attackers may attempt to:

- Trick users into installing fake packages.
- Add malicious repositories.
- Replace trusted software with backdoored versions.

Defenders should:

- Use official repositories.
- Verify repository sources.
- Keep systems updated.
- Remove unnecessary software.

---

# ⚠ Common Beginner Mistakes

❌ Running `apt upgrade` without first using `apt update`.

❌ Installing software from untrusted websites.

❌ Ignoring security updates.

❌ Deleting dependencies manually.

❌ Forgetting `sudo` when installing packages.

---

# 🧪 Hands-on Lab

> **Note:** These commands may download software from the internet.

```bash
sudo apt update

apt search nmap

apt show nmap

sudo apt install tree

tree

sudo apt remove tree

sudo apt autoremove

apt list --installed | grep tree
```

---

# 🎯 Mini Challenge

1.

Refresh the package list.

2.

Search for:

```text
curl
```

3.

Display package information.

4.

Install:

```text
tree
```

5.

Verify it is installed.

6.

Remove it.

7.

Run:

```bash
sudo apt autoremove
```

---

# 📋 Command Cheat Sheet

| Command | Purpose |
|----------|----------|
| `apt update` | Refresh package list |
| `apt upgrade` | Upgrade installed packages |
| `apt install` | Install software |
| `apt remove` | Remove software |
| `apt purge` | Remove software and configuration |
| `apt autoremove` | Remove unused dependencies |
| `apt search` | Search packages |
| `apt show` | Package information |
| `apt list --installed` | List installed packages |
| `apt list --upgradable` | List available upgrades |
| `dpkg -i` | Install local `.deb` package |
| `dpkg -l` | List installed packages |

---

# 🧠 Memory Trick

```
update

Refresh package list
```

↓

```
upgrade

Install updates
```

↓

```
install

Add software
```

↓

```
remove

Remove software
```

↓

```
purge

Remove everything
```

↓

```
autoremove

Clean leftovers
```

---

# ❓ Interview Questions

1. What is a Linux package?

2. What is APT?

3. What is the difference between `apt update` and `apt upgrade`?

4. What is a repository?

5. Why should official repositories be preferred?

6. What is the difference between `apt remove` and `apt purge`?

7. What is `apt autoremove` used for?

8. What is `dpkg`?

9. Where are APT repositories configured?

10. Why are software updates important in cybersecurity?

---

# 🎯 Key Takeaways

✅ A package contains software and its supporting files.

✅ APT is Kali Linux's primary package manager.

✅ Repositories provide trusted software and updates.

✅ `apt update` refreshes package information.

✅ `apt upgrade` installs available updates.

✅ `dpkg` is the underlying package management tool.

✅ Keeping software updated is a critical cybersecurity practice.

---

# 📚 Next Lesson

➡ **08 - Bash Shell Basics**

Topics include:

- What is Bash?
- Shell Variables
- Command History
- Aliases
- Wildcards
- Command Chaining (`&&`, `;`, `||`)
- Basic Bash Scripting
- Input & Output
- Command Substitution

---

<div align="center">

## ⭐ "A secure system isn't just built with good software—it is maintained through timely updates and trusted sources."

**Happy Learning! 🐧**

</div>
