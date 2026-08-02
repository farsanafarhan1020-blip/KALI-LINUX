<div align="center">

# 🐉 Kali Linux Masterclass
## 📘 Phase 1 – Linux Fundamentals

# 04 - Linux Permissions

*"Security begins with controlling who can access what."*

![Linux](https://img.shields.io/badge/Linux-Permissions-FCC624?style=for-the-badge&logo=linux)
![Kali](https://img.shields.io/badge/Kali-Linux-557C94?style=for-the-badge&logo=kalilinux)
![Cybersecurity](https://img.shields.io/badge/Cyber-Security-red?style=for-the-badge)

</div>

---

# 📚 Table of Contents

- Introduction
- Why Permissions Matter
- Users, Groups & Others
- Permission Types
- Viewing Permissions
- Understanding `ls -l`
- Permission Symbols
- Numeric Permissions
- chmod
- chown
- chgrp
- Root User
- Special Permission Bits
- Real-World Examples
- Best Practices
- Hands-on Lab
- Cheat Sheet
- Interview Questions
- Key Takeaways

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

✅ Understand Linux file permissions

✅ Read permission strings

✅ Change permissions using `chmod`

✅ Change ownership using `chown`

✅ Change groups using `chgrp`

✅ Understand the importance of the root user

---

# 🌟 Introduction

Linux is a **multi-user operating system**.

Multiple users can work on the same computer at the same time.

Without permissions:

- Anyone could delete important files.
- Anyone could modify system settings.
- Anyone could read confidential data.

Permissions prevent this by controlling **who can read, write, or execute files and directories**.

---

# 🛡 Why Permissions Matter

Imagine a company server:

```
Employees
│
├── HR Files
├── Payroll
├── Customer Data
└── System Files
```

Should every employee have access to everything?

❌ No.

Permissions ensure that only authorized users can access sensitive resources.

---

# 👥 Understanding Users

Linux divides access into three categories:

```
             File
               │
     ┌─────────┼─────────┐
     │         │         │
   User      Group     Others
 (Owner)   (Members)  (Everyone Else)
```

### 1. User (Owner)

The person who owns the file.

---

### 2. Group

A collection of users who share permissions.

Example:

```
Developers

HR

NetworkAdmins

SecurityTeam
```

---

### 3. Others

Everyone else on the system.

---

# 🔐 Permission Types

Linux has three basic permissions.

| Symbol | Name | Meaning |
|--------|------|---------|
| r | Read | View file contents |
| w | Write | Modify the file |
| x | Execute | Run a file as a program or script |

---

# 📖 Viewing Permissions

Use:

```bash
ls -l
```

Example:

```text
-rwxr-xr-- 1 farhan security 2048 Jul 30 script.sh
```

---

# 🧠 Breaking It Down

```
-rwxr-xr--
││││││││││
││││││││└── Others
│││││└──── Group
│└──────── User
└───────── File Type
```

---

## File Type

| Symbol | Meaning |
|---------|----------|
| - | File |
| d | Directory |
| l | Symbolic Link |

---

## User Permissions

```
rwx
```

Owner can:

✔ Read

✔ Write

✔ Execute

---

## Group Permissions

```
r-x
```

Group can:

✔ Read

❌ Write

✔ Execute

---

## Others

```
r--
```

Others can:

✔ Read

❌ Write

❌ Execute

---

# 📊 Permission Diagram

```
-rwxr-xr--

-

File

rwx

Owner

r-x

Group

r--

Others
```

---

# 🔢 Numeric Permissions

Each permission has a number.

| Permission | Value |
|------------|------|
| Read | 4 |
| Write | 2 |
| Execute | 1 |

Add them together.

---

## Examples

### 7

```
4 + 2 + 1

=

rwx
```

---

### 6

```
4 + 2

=

rw-
```

---

### 5

```
4 + 1

=

r-x
```

---

### 4

```
4

=

r--
```

---

### 0

```
---

No Permission
```

---

# 🧠 Common Permission Values

## 777

```
rwxrwxrwx
```

Everyone can do everything.

⚠ Dangerous.

---

## 755

```
rwxr-xr-x
```

Owner:

Read

Write

Execute

Others:

Read

Execute

Most common for directories and executable files.

---

## 644

```
rw-r--r--
```

Owner:

Read

Write

Everyone else:

Read Only

Common for documents and configuration files.

---

## 600

```
rw-------
```

Private file.

Only the owner has access.

Ideal for sensitive information.

---

# ⚙ chmod

Changes permissions.

---

## Symbolic Method

```bash
chmod u+x script.sh
```

Meaning:

```
u

User

+

Add

x

Execute
```

---

Remove permission

```bash
chmod g-w file.txt
```

---

Grant read permission to others

```bash
chmod o+r notes.txt
```

---

## Numeric Method

```bash
chmod 755 script.sh
```

```bash
chmod 644 config.txt
```

```bash
chmod 600 secrets.txt
```

---

# 👑 chown

Changes file ownership.

Syntax

```bash
sudo chown user file
```

Example

```bash
sudo chown farhan report.txt
```

---

Change owner and group

```bash
sudo chown farhan:security report.txt
```

---

# 👥 chgrp

Changes the file's group.

```bash
sudo chgrp security report.txt
```

---

# 👑 Root User

Linux has a special administrator account.

```
root
```

Root can:

✔ Read everything

✔ Write everything

✔ Execute everything

✔ Install software

✔ Create users

✔ Delete users

✔ Modify system settings

Use root carefully because mistakes can affect the entire system.

---

# 🚨 Special Permission Bits

As you progress, you'll encounter:

- SUID
- SGID
- Sticky Bit

These provide special permission behavior and are commonly discussed in cybersecurity.

We'll cover them in a later lesson.

---

# 🌍 Real-World Cybersecurity Example

A penetration tester uploads a script:

```bash
exploit.sh
```

Running it gives:

```
Permission denied
```

Why?

The execute permission is missing.

Solution:

```bash
chmod +x exploit.sh

./exploit.sh
```

Understanding permissions helps identify and solve such issues quickly.

---

# ⚠ Common Beginner Mistakes

❌ Using `777` on everything.

❌ Running as root unnecessarily.

❌ Forgetting execute permission for scripts.

❌ Accidentally changing ownership of system files.

---

# 🛡 Security Best Practices

✔ Follow the Principle of Least Privilege.

✔ Give users only the permissions they need.

✔ Avoid using `777`.

✔ Keep sensitive files as `600`.

✔ Verify permissions before sharing files.

---

# 💼 Industry Tip

Most Linux administrators avoid `chmod 777`.

Instead, they grant only the minimum permissions required.

This reduces the risk of accidental modification or unauthorized access.

---

# 🧪 Hands-on Lab

```bash
mkdir PermissionLab

cd PermissionLab

touch script.sh

touch notes.txt

ls -l

chmod 755 script.sh

chmod 644 notes.txt

ls -l

chmod u+x script.sh

ls -l
```

Observe how the permission strings change after each command.

---

# 🎯 Mini Challenge

Create:

```bash
touch secrets.txt
```

Set the following permissions:

```
Owner

Read

Write

Others

No Access
```

Hint:

```
600
```

Now verify using:

```bash
ls -l
```

---

# 📋 Cheat Sheet

| Command | Purpose |
|----------|---------|
| ls -l | View permissions |
| chmod | Change permissions |
| chmod 755 | rwxr-xr-x |
| chmod 644 | rw-r--r-- |
| chmod 600 | rw------- |
| chown | Change owner |
| chgrp | Change group |

---

# 🧠 Memory Trick

```
Read

4

Write

2

Execute

1
```

```
7 = 4+2+1

rwx
```

```
6 = 4+2

rw-
```

```
5 = 4+1

r-x
```

```
4 = Read Only

r--
```

---

# ❓ Interview Questions

1. What are Linux file permissions?

2. Explain the difference between User, Group and Others.

3. What does `chmod` do?

4. What does `755` mean?

5. What does `644` mean?

6. Why is `777` considered dangerous?

7. What is the root user?

8. Explain the Principle of Least Privilege.

---

# 🎯 Key Takeaways

✅ Linux uses a permission-based security model.

✅ Every file belongs to a user and a group.

✅ Three basic permissions exist: Read, Write and Execute.

✅ `chmod` changes permissions.

✅ `chown` changes ownership.

✅ `chgrp` changes groups.

✅ Avoid using `777` unless absolutely necessary.

✅ Understanding permissions is essential for Linux administration and cybersecurity.

---

# 📚 Next Lesson

➡ **05 - Linux Users & Groups**

Topics include:

- Creating users
- Deleting users
- Switching users
- Groups
- Password management
- sudo
- id
- whoami
- passwd
- useradd
- usermod

---

<div align="center">

## ⭐ "The strongest security isn't built by giving everyone access—it's built by giving only the right people the right access."

**Happy Learning! 🐧**

</div>
