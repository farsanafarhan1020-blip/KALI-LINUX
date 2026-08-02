<div align="center">

# 🐉 Kali Linux Masterclass
## 📘 Phase 1 – Linux Fundamentals

# 05 - Linux Users & Groups

*"Linux is built for multiple users. Understanding users and groups is the foundation of Linux security."*

![Linux](https://img.shields.io/badge/Linux-Users%20%26%20Groups-FCC624?style=for-the-badge&logo=linux)
![Kali](https://img.shields.io/badge/Kali-Linux-557C94?style=for-the-badge&logo=kalilinux)
![Cybersecurity](https://img.shields.io/badge/Cyber-Security-red?style=for-the-badge)

</div>

---

# 📚 Table of Contents

- Introduction
- What is a User?
- Types of Users
- What is a Group?
- Why Groups are Important
- User Information Files
- Essential Commands
- Creating Users
- Modifying Users
- Deleting Users
- Switching Users
- Password Management
- sudo
- Best Practices
- Cybersecurity Perspective
- Hands-on Lab
- Cheat Sheet
- Interview Questions
- Key Takeaways

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

✅ Understand Linux users

✅ Understand Linux groups

✅ View user information

✅ Create and manage users

✅ Create and manage groups

✅ Use sudo safely

---

# 🌟 Introduction

Unlike Windows Home editions, Linux was designed from the beginning as a **multi-user operating system**.

Many users can use the same Linux system while each user has:

- Their own files
- Their own settings
- Their own permissions
- Their own home directory

This separation improves both **security** and **system organization**.

---

# 👤 What is a User?

A **user** is an account that allows someone to log in and use the operating system.

Each user has:

- Username
- Password
- Home directory
- User ID (UID)
- Default shell
- Group membership

Example:

```
Username

farhan

↓

Logs into Linux

↓

Own Home Folder

↓

/home/farhan
```

---

# 👥 Types of Users

## 1️⃣ Root User

```
root
```

The administrator.

Has unrestricted access to the system.

UID:

```
0
```

---

## 2️⃣ Regular Users

Normal users for daily work.

Examples:

```
alice

bob

farhan
```

These users have limited permissions.

---

## 3️⃣ System Users

Created automatically by Linux.

Used by services and applications.

Examples:

```
www-data

mysql

nobody

daemon
```

Normally these users cannot log in interactively.

---

# 📂 What is a Group?

A **group** is a collection of users.

Instead of assigning permissions to each user individually, permissions can be assigned to the entire group.

```
Developers
│
├── Alice
├── Bob
└── Charlie
```

Every member inherits the group's permissions.

---

# 💡 Why Groups Matter

Imagine a company:

```
HR

Developers

Security

Managers
```

Instead of assigning permissions to every employee one by one, assign permissions to the department's group.

This makes administration much easier.

---

# 📁 Important User Files

## /etc/passwd

Stores user account information.

Example:

```
farhan:x:1000:1000:Farhan:/home/farhan:/bin/bash
```

Contains:

- Username
- UID
- GID
- Home directory
- Default shell

Passwords are **not** stored here.

---

## /etc/shadow

Stores encrypted passwords.

Only root can read this file.

---

## /etc/group

Stores information about groups.

Example:

```
developers:x:1001:farhan,alice,bob
```

---

# 🆔 id

Displays user information.

```bash
id
```

Example:

```
uid=1000(farhan)

gid=1000(farhan)

groups=1000(farhan),27(sudo)
```

---

# 👤 whoami

Displays the current username.

```bash
whoami
```

Output:

```
farhan
```

---

# 📍 who

Shows users currently logged in.

```bash
who
```

---

# 👥 groups

Shows the groups the current user belongs to.

```bash
groups
```

Example:

```
farhan sudo developers
```

---

# ➕ useradd

Creates a new user.

```bash
sudo useradd john
```

---

Create a home directory automatically.

```bash
sudo useradd -m john
```

---

Specify a shell.

```bash
sudo useradd -m -s /bin/bash john
```

---

# 🔑 passwd

Sets or changes a user's password.

```bash
sudo passwd john
```

Linux asks:

```
New password:

Retype password:
```

---

# ✏ usermod

Modifies an existing user.

Add a user to a group:

```bash
sudo usermod -aG developers john
```

Explanation:

```
-a

Append

G

Group
```

Always use `-aG` together to avoid removing the user from existing groups.

---

# ➖ userdel

Deletes a user.

```bash
sudo userdel john
```

Delete the user and their home directory:

```bash
sudo userdel -r john
```

---

# 👥 groupadd

Creates a new group.

```bash
sudo groupadd developers
```

---

# 🗑 groupdel

Deletes a group.

```bash
sudo groupdel developers
```

---

# 🔄 su (Switch User)

Switch to another user.

```bash
su john
```

Switch to root.

```bash
su -
```

Linux requests the target user's password.

---

# ⚡ sudo

Runs a command with administrator privileges.

Example:

```bash
sudo apt update
```

Instead of logging in as root, Linux temporarily grants administrative rights for that command.

---

## Why sudo is Better than Root

✔ Better security

✔ Better logging

✔ Reduced risk of accidental damage

✔ Least privilege

---

# 🧠 Understanding UID

Every user has a unique User ID.

```
Root

↓

UID 0
```

Normal users:

```
1000+

```

System users:

Usually

```
1–999
```

(Exact ranges may vary by Linux distribution.)

The operating system identifies users internally by **UID**, not by username.

---

# 🌍 Real-World Cybersecurity Example

Imagine a Security Operations Center.

```
SOC Team

↓

security Group

↓

Read Access

↓

/var/log
```

Only members of the **security** group can view sensitive logs.

This prevents unauthorized users from accessing critical information.

---

# 🛡 Cybersecurity Perspective

Attackers often attempt to:

- Escalate privileges
- Steal passwords
- Add backdoor users
- Add themselves to privileged groups
- Abuse sudo privileges

Defenders monitor:

- New user creation
- Group changes
- Failed login attempts
- Sudo usage
- Password changes

---

# ⚠ Common Beginner Mistakes

❌ Logging in as root for everyday work.

❌ Forgetting `-m` with `useradd`.

❌ Forgetting `-a` when using `usermod -G`.

❌ Giving every user sudo access.

❌ Weak passwords.

---

# 🛡 Security Best Practices

✔ Use strong passwords.

✔ Use sudo instead of logging in as root.

✔ Follow the Principle of Least Privilege.

✔ Regularly review user accounts.

✔ Remove unused accounts.

✔ Monitor sudo activity.

---

# 💼 Industry Tip

Large organizations rarely assign permissions directly to individual users.

Instead, they:

```
Create Groups

↓

Assign Permissions

↓

Add Users to Groups
```

This makes management much simpler.

---

# 🧪 Hands-on Lab

```bash
whoami

id

groups

sudo groupadd developers

sudo useradd -m john

sudo passwd john

sudo usermod -aG developers john

id john

groups john

sudo userdel -r john

sudo groupdel developers
```

---

# 🎯 Mini Challenge

1.

Find your username.

2.

Display your UID.

3.

List your groups.

4.

Find your current shell.

5.

Display the contents of:

```
/etc/passwd
```

6.

Find your own user entry using:

```bash
grep
```

---

# 📋 Command Cheat Sheet

| Command | Purpose |
|----------|----------|
| whoami | Current user |
| who | Logged-in users |
| id | User information |
| groups | Show groups |
| useradd | Create user |
| usermod | Modify user |
| userdel | Delete user |
| passwd | Change password |
| groupadd | Create group |
| groupdel | Delete group |
| su | Switch user |
| sudo | Run as administrator |

---

# 🧠 Memory Trick

```
whoami

Who am I?
```

```
id

Identity
```

```
groups

Group Membership
```

```
passwd

Password
```

```
sudo

Super User Do
```

---

# ❓ Interview Questions

1. What is a Linux user?

2. What is a Linux group?

3. What is the difference between root and a regular user?

4. What does `sudo` do?

5. Why is `sudo` preferred over logging in as root?

6. What information is stored in `/etc/passwd`?

7. What is `/etc/shadow`?

8. Explain UID and GID.

9. What does `usermod -aG` do?

10. What is the Principle of Least Privilege?

---

# 🎯 Key Takeaways

✅ Linux supports multiple users.

✅ Every user has a unique UID.

✅ Groups simplify permission management.

✅ `sudo` provides temporary administrative privileges.

✅ `/etc/passwd`, `/etc/shadow`, and `/etc/group` are essential user management files.

✅ Proper user management is a fundamental part of Linux security.

---

# 📚 Next Lesson

➡ **06 - Linux Processes & Services**

Topics include:

- Running Processes
- Process IDs (PID)
- ps
- top
- htop
- kill
- killall
- nice
- jobs
- fg
- bg
- systemctl
- Services
- Daemons

---

<div align="center">

## ⭐ "Managing users is managing trust. A secure Linux system begins with proper user administration."

**Happy Learning! 🐧**

</div>
