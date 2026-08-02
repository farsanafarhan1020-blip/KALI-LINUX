<div align="center">

# 🐉 Kali Linux Masterclass
## 📘 Phase 1 – Linux Fundamentals

# 02 - Linux Terminal & File System

*"The terminal is where Linux truly comes alive."*

![Linux](https://img.shields.io/badge/Linux-Terminal-FCC624?style=for-the-badge&logo=linux)
![Kali](https://img.shields.io/badge/Kali-Linux-557C94?style=for-the-badge&logo=kalilinux)
![Level](https://img.shields.io/badge/Level-Beginner-success?style=for-the-badge)

</div>

---

# 📚 Table of Contents

- Introduction
- What is the Terminal?
- Why Learn the Terminal?
- GUI vs CLI
- Understanding the Linux Prompt
- Linux File System
- Important Directories
- Absolute vs Relative Paths
- Essential Navigation Commands
- Common Mistakes
- Real-World Example
- Hands-on Lab
- Cheat Sheet
- Interview Questions
- Key Takeaways

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

✅ Understand the Linux Terminal

✅ Navigate through directories

✅ Understand the Linux file system

✅ Use navigation commands confidently

✅ Understand absolute and relative paths

---

# 🌟 Introduction

One of the biggest differences between Windows and Linux is the **Terminal**.

Most cybersecurity professionals spend a large portion of their day working inside the terminal because it is faster, more powerful, and allows automation.

Learning the terminal is one of the most valuable Linux skills you can develop.

---

# 🖥 What is the Terminal?

The **Terminal** is a text-based interface used to communicate directly with the operating system.

Instead of clicking icons with a mouse, you type commands.

Example:

```bash
pwd
```

The operating system receives the command, processes it, and displays the result.

---

# 🧠 How Does the Terminal Work?

```
+-------------+
|   Keyboard  |
+-------------+
       │
       ▼
+----------------+
|     Shell      |
| (Bash / Zsh)   |
+----------------+
       │
       ▼
+----------------+
| Linux Kernel   |
+----------------+
       │
       ▼
+----------------+
| Hardware       |
+----------------+
```

### Components

### Keyboard

You type commands.

↓

### Shell

Interprets your commands.

↓

### Kernel

Communicates with hardware.

↓

### Hardware

Performs the requested task.

---

# 💡 What is a Shell?

A **Shell** is a command interpreter.

It reads the command you type and tells the operating system what to do.

Common shells include:

- Bash (Most Popular)
- Zsh
- Fish
- Sh

Kali Linux uses **Bash** by default in most installations.

---

# ⚔ GUI vs CLI

| GUI | CLI |
|------|-----|
| Graphical Interface | Command Line Interface |
| Uses Mouse | Uses Keyboard |
| Easy for Beginners | Faster for Professionals |
| Slower for Repetitive Tasks | Easy to Automate |
| Limited Control | Full Control |

---

# 🤔 Why Do Cybersecurity Professionals Prefer the Terminal?

✔ Faster

✔ Easy to automate

✔ Works remotely using SSH

✔ Consumes fewer resources

✔ Many security tools are terminal-based

---

# 💻 Understanding the Prompt

Example:

```text
farhan@kali:~$
```

Breakdown:

```
farhan
│
└── Current User

@

kali
│
└── Hostname

:

~
│
└── Home Directory

$
│
└── Normal User
```

If the prompt ends with:

```text
#
```

You are operating as the **root user**.

Root has unrestricted access to the system.

---

# 🌳 Linux File System

Unlike Windows:

```
C:\
D:\
E:\
```

Linux has **one single directory tree**.

Everything starts from:

```
/
```

This is called the **Root Directory**.

---

# 📂 Linux Directory Structure

```
                    /
      ┌─────────────┼──────────────┐
      │             │              │
    home          etc            var
      │
   farhan
      │
 ┌────┼───────────────┐
 │    │       │       │
Docs Downloads Desktop Pictures
```

Every file and directory exists somewhere under `/`.

---

# 📁 Important Linux Directories

| Directory | Purpose |
|------------|----------|
| / | Root directory |
| /home | User home folders |
| /root | Root user's home |
| /etc | Configuration files |
| /bin | Essential system commands |
| /usr | Installed applications |
| /var | Logs and variable data |
| /tmp | Temporary files |
| /dev | Device files |
| /proc | Running process information |
| /opt | Optional software |

---

# 📍 pwd (Print Working Directory)

## 📖 What is it?

Displays your current location in the Linux file system.

---

## Syntax

```bash
pwd
```

---

## Example

```bash
pwd
```

Output

```text
/home/farhan
```

---

## Internal Working

The shell asks the kernel for the current working directory associated with your process and prints the absolute path.

---

## Cybersecurity Importance

Before deleting files or editing configurations, always verify your location using `pwd`.

---

# 📂 ls (List)

Displays files and directories.

---

## Syntax

```bash
ls
```

---

## Example

```bash
Desktop
Documents
Downloads
Pictures
```

---

## Useful Options

### Detailed List

```bash
ls -l
```

---

### Show Hidden Files

```bash
ls -a
```

---

### Detailed + Hidden

```bash
ls -la
```

---

### Recursive Listing

```bash
ls -R
```

Lists all files and folders, including the contents of every subdirectory.

---

# 📁 cd (Change Directory)

Changes the current directory.

---

## Enter a Folder

```bash
cd Documents
```

---

## Go Back One Directory

```bash
cd ..
```

---

## Go Home

```bash
cd
```

or

```bash
cd ~
```

---

## Go to Root

```bash
cd /
```

---

# 🌍 Absolute vs Relative Path

## Absolute Path

Starts from the root directory.

Example

```bash
/home/farhan/Documents
```

Works no matter where you currently are.

---

## Relative Path

Starts from your current directory.

Example

```bash
Documents
```

Works only if the folder exists inside your current location.

---

# 📂 mkdir

Creates a new directory.

```bash
mkdir CyberLab
```

---

# 📄 touch

Creates an empty file.

```bash
touch notes.txt
```

---

# 📋 cp

Copies files.

```bash
cp notes.txt backup.txt
```

---

# 🚚 mv

Moves or renames files.

Rename

```bash
mv old.txt new.txt
```

Move

```bash
mv notes.txt Documents/
```

---

# ❌ rm

Deletes files.

```bash
rm notes.txt
```

⚠ Deleted files usually cannot be recovered easily.

Always verify before pressing Enter.

---

# 🗑 rmdir

Deletes an empty directory.

```bash
rmdir TestFolder
```

---

# 📖 cat

Displays the contents of a file.

```bash
cat notes.txt
```

---

# 🧠 Memory Trick

```
pwd     → Where am I?

ls      → What is here?

cd      → Go somewhere

mkdir   → Make folder

touch   → Make file

cp      → Copy

mv      → Move/Rename

rm      → Remove

cat     → Read file
```

---

# 🌍 Real-World Cybersecurity Example

Imagine you connect to a remote Linux server using SSH.

Before editing configuration files, you might run:

```bash
pwd

ls

cd /etc

ls
```

This confirms your current location and helps avoid modifying the wrong files.

---

# ⚠ Common Beginner Mistakes

❌ Forgetting Linux is case-sensitive.

```
Documents
```

is different from

```
documents
```

---

❌ Forgetting your current directory.

Always check:

```bash
pwd
```

---

❌ Accidentally deleting important files with:

```bash
rm
```

---

❌ Confusing `/` (root directory) with `~` (home directory).

---

# 💼 Industry Tip

Experienced Linux administrators often type:

```bash
pwd
```

before running commands such as:

```bash
rm
mv
cp
```

to avoid making changes in the wrong directory.

---

# 🧪 Hands-on Lab

Complete the following:

```bash
cd ~

mkdir LinuxPractice

cd LinuxPractice

touch day1.txt day2.txt day3.txt

mv day3.txt practice.txt

cp day1.txt backup_day1.txt

pwd

ls

ls -la

ls -R
```

---

# 🎯 Mini Challenge

Without looking at the notes:

1. Create a folder called **Projects**

2. Enter it

3. Create two files

```
project1.txt
project2.txt
```

4. Rename one file.

5. Copy the second file.

6. Display your current directory.

7. Show all hidden files.

---

# 📋 Command Cheat Sheet

| Command | Description |
|----------|-------------|
| pwd | Show current directory |
| ls | List files |
| ls -l | Detailed list |
| ls -a | Hidden files |
| ls -la | Detailed + Hidden |
| ls -R | Recursive list |
| cd | Change directory |
| cd .. | Go back |
| cd ~ | Home directory |
| cd / | Root directory |
| mkdir | Create folder |
| touch | Create file |
| cp | Copy |
| mv | Move/Rename |
| rm | Delete file |
| rmdir | Delete empty folder |
| cat | Display file |

---

# ❓ Interview Questions

### What is the difference between CLI and GUI?

### What is the root directory?

### Explain the difference between an absolute path and a relative path.

### What does `pwd` do?

### What is the purpose of `ls -la`?

### What does `cd ..` do?

### Why is Linux case-sensitive?

### What is the difference between `/` and `~`?

---

# 🎯 Key Takeaways

✅ Linux uses a single hierarchical file system.

✅ The terminal is the fastest way to interact with Linux.

✅ Learn navigation before learning security tools.

✅ Always know your current directory.

✅ Understand absolute and relative paths.

✅ Small navigation mistakes can lead to major system changes.

---

# 📚 Next Lesson

➡ **03 - Working with Files & Text**

Topics include:

- echo
- cat (Advanced)
- nano
- less
- head
- tail
- wc
- grep
- Redirection (`>` and `>>`)
- Pipes (`|`)

These commands are heavily used by Linux administrators, SOC analysts, penetration testers, and cybersecurity professionals every day.

---

<div align="center">

## ⭐ "Master navigation today, master Linux tomorrow."

**Happy Learning! 🐧**

</div>
