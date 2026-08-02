<div align="center">

# 🐉 Kali Linux Masterclass
## 📘 Phase 1 – Linux Fundamentals

# 10 - Linux File System Deep Dive

*"Everything in Linux is a file—but what does that really mean?"*

![Linux](https://img.shields.io/badge/Linux-File%20System-FCC624?style=for-the-badge&logo=linux)
![Kali](https://img.shields.io/badge/Kali-Linux-557C94?style=for-the-badge&logo=kalilinux)
![Level](https://img.shields.io/badge/Deep%20Dive-Intermediate-blue?style=for-the-badge)

</div>

---

# 📚 Table of Contents

- Introduction
- What is a File System?
- How Linux Stores Files
- Understanding Inodes
- File Metadata
- Hard Links
- Symbolic Links
- Mount Points
- Virtual File Systems
- The `/proc` File System
- The `/sys` File System
- The `/dev` Directory
- File Descriptors
- Disk Usage Commands
- Cybersecurity Perspective
- Hands-on Lab
- Cheat Sheet
- Interview Questions
- Key Takeaways

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

✅ Understand how Linux stores files

✅ Explain what an inode is

✅ Differentiate hard links and symbolic links

✅ Understand mount points

✅ Explore `/proc`, `/sys`, and `/dev`

✅ Use disk usage commands

---

# 🌟 Introduction

When you create a file in Linux, you're not just saving data.

The operating system stores:

- File name
- File location
- Owner
- Permissions
- Timestamps
- Size
- Physical storage information

Linux organizes all of this using a **file system**.

Understanding how it works internally is extremely valuable for:

- System Administration
- Digital Forensics
- Malware Analysis
- Incident Response
- Ethical Hacking

---

# 📂 What is a File System?

A **file system** is the method an operating system uses to organize, store, and retrieve files on a storage device.

Think of a library:

```
Library
│
├── Shelves
├── Books
├── Book Numbers
└── Catalog
```

Linux works similarly:

```
Disk
│
├── Directories
├── Files
├── Inodes
└── Metadata
```

---

# 💽 How Linux Stores Files

When you save a file:

```
Create File

↓

Allocate Storage Blocks

↓

Create Inode

↓

Store Metadata

↓

Create Filename

↓

Done
```

The **file name** and the **file contents** are stored separately.

This is one of the most important Linux concepts.

---

# 🧠 What is an Inode?

An **inode (Index Node)** is a data structure that stores information **about** a file.

An inode does **not** store the filename.

It stores metadata such as:

- File size
- Owner
- Group
- Permissions
- Timestamps
- Block locations
- Link count

Every file has an inode number.

---

# 🗂 Inode Diagram

```
Filename

notes.txt

↓

Directory Entry

↓

Inode #12345

↓

Metadata

↓

Disk Blocks

↓

Actual File Data
```

Notice that the filename points to the inode, and the inode points to the file's data.

---

# 🔍 View Inode Numbers

```bash
ls -i
```

Example:

```text
12345 notes.txt
```

To view detailed metadata:

```bash
stat notes.txt
```

Example output includes:

- File size
- Permissions
- Owner
- Access time
- Modify time
- Change time
- Inode number

---

# 📋 File Metadata

Metadata is "data about data."

Common metadata:

| Property | Description |
|----------|-------------|
| Owner | File owner |
| Group | Group owner |
| Permissions | Access rights |
| Size | File size |
| Inode | Unique identifier |
| Access Time (atime) | Last read |
| Modify Time (mtime) | Last content modification |
| Change Time (ctime) | Last metadata change |

---

# 🔗 Hard Links

A **hard link** creates another directory entry that points to the **same inode**.

Create:

```bash
ln notes.txt backup.txt
```

Diagram:

```
notes.txt
      │
      ▼
   Inode 12345
      ▲
      │
backup.txt
```

Both names refer to the same file data.

If one filename is deleted, the data still exists as long as another hard link points to the inode.

---

## Characteristics

✔ Shares the same inode

✔ Shares the same data

✔ Deleting one name does not remove the data immediately

❌ Cannot span different file systems

❌ Usually cannot be created for directories (except by the system)

---

# 🔗 Symbolic Links (Soft Links)

A symbolic link is a special file that stores the **path** to another file.

Create:

```bash
ln -s notes.txt shortcut.txt
```

Diagram:

```
shortcut.txt

↓

notes.txt

↓

Inode

↓

Data
```

Unlike hard links, symbolic links have their own inode and simply point to another path.

---

## Characteristics

✔ Can link across file systems

✔ Can point to directories

✔ Easier to recognize (`ls -l` shows `->`)

❌ Breaks if the original target is removed or renamed

---

# ⚖ Hard Link vs Symbolic Link

| Feature | Hard Link | Symbolic Link |
|----------|-----------|---------------|
| Same inode | ✅ | ❌ |
| Can cross file systems | ❌ | ✅ |
| Can link directories | Usually No | Yes |
| Breaks if original removed | ❌ | ✅ |
| Stores file path | ❌ | ✅ |

---

# 📍 Mount Points

Linux combines storage devices into one directory tree.

Example:

```
/

├── home

├── media

│      └── USB Drive

└── mnt
```

A **mount point** is a directory where another storage device is attached.

View mounted file systems:

```bash
mount
```

or

```bash
findmnt
```

Check disk usage:

```bash
df -h
```

---

# 📂 Virtual File Systems

Some Linux directories do **not** store normal files.

Instead, they provide information generated by the kernel.

Examples:

```
/proc

/sys

/dev
```

---

# 🖥 The `/proc` File System

`/proc` is a virtual file system that provides information about:

- Running processes
- CPU
- Memory
- Kernel settings

Example:

```bash
ls /proc
```

View CPU information:

```bash
cat /proc/cpuinfo
```

View memory information:

```bash
cat /proc/meminfo
```

---

# ⚙ The `/sys` File System

`/sys` provides information about:

- Hardware devices
- Drivers
- Kernel objects

Example:

```bash
ls /sys
```

System administrators use it for hardware inspection and tuning.

---

# 💻 The `/dev` Directory

Linux represents hardware devices as files.

Examples:

| Device | Description |
|---------|-------------|
| `/dev/sda` | Hard disk |
| `/dev/null` | Discards all data written to it |
| `/dev/random` | Random data source |
| `/dev/urandom` | Pseudo-random data source |
| `/dev/tty` | Current terminal |

Example:

```bash
echo "Hello" > /dev/null
```

The data is discarded.

---

# 📄 File Descriptors

Every running process uses **file descriptors** to access files and streams.

Standard file descriptors:

| Number | Name |
|---------|------|
| 0 | Standard Input (stdin) |
| 1 | Standard Output (stdout) |
| 2 | Standard Error (stderr) |

Example:

```bash
ls > files.txt
```

Redirects **stdout (1)** to a file.

Redirect errors:

```bash
ls missingfile 2> errors.txt
```

Redirect both output and errors:

```bash
ls . missingfile > output.txt 2>&1
```

---

# 💾 Disk Usage Commands

## Display Disk Space

```bash
df -h
```

Shows available and used disk space.

---

## Display Directory Size

```bash
du -sh Documents
```

---

## View Mounted File Systems

```bash
findmnt
```

---

# 🌍 Real-World Cybersecurity Example

During a forensic investigation:

- `stat` checks timestamps.
- `ls -i` compares inode numbers.
- `/proc` helps identify running processes.
- `/dev` helps locate storage devices.
- `df` confirms mounted disks.

These tools help investigators understand what happened on a compromised system.

---

# 🛡 Cybersecurity Perspective

Attackers may:

- Hide files using symbolic links.
- Manipulate timestamps.
- Mount malicious storage devices.
- Create persistence through unusual locations.

Defenders inspect:

- Inodes
- File metadata
- Mount points
- Running processes
- Device files

---

# ⚠ Common Beginner Mistakes

❌ Thinking the filename is stored inside the inode.

❌ Confusing hard links with symbolic links.

❌ Editing files in `/proc`.

❌ Deleting symbolic link targets without realizing links will break.

❌ Ignoring metadata during investigations.

---

# 💼 Industry Tip

Digital forensics professionals rely heavily on:

- `stat`
- `ls -i`
- `findmnt`
- `df`
- `du`
- `/proc`

These tools reveal valuable evidence during incident response.

---

# 🧪 Hands-on Lab

```bash
mkdir FileSystemLab

cd FileSystemLab

echo "Linux" > notes.txt

ls -i

stat notes.txt

ln notes.txt hardlink.txt

ln -s notes.txt symlink.txt

ls -li

df -h

du -sh .

findmnt

cat /proc/cpuinfo

cat /proc/meminfo

ls /dev | head
```

---

# 🎯 Mini Challenge

1.

Create:

```text
notes.txt
```

2.

Find its inode.

3.

Create:

- One hard link
- One symbolic link

4.

Delete the original file.

5.

Observe what happens to both links.

6.

Display disk usage.

7.

Display your mounted file systems.

---

# 📋 Command Cheat Sheet

| Command | Purpose |
|----------|----------|
| `ls -i` | Show inode numbers |
| `stat` | Display file metadata |
| `ln` | Create hard link |
| `ln -s` | Create symbolic link |
| `df -h` | Show disk usage |
| `du -sh` | Show directory size |
| `mount` | Show mounted file systems |
| `findmnt` | Display mount hierarchy |
| `cat /proc/cpuinfo` | CPU information |
| `cat /proc/meminfo` | Memory information |

---

# 🧠 Memory Trick

```
Inode

Stores Metadata
```

↓

```
Hard Link

Same Inode
```

↓

```
Soft Link

Points to Path
```

↓

```
/proc

Process & Kernel Information
```

↓

```
/sys

Hardware Information
```

↓

```
/dev

Device Files
```

---

# ❓ Interview Questions

1. What is a file system?

2. What is an inode?

3. Does an inode store the filename?

4. What is the difference between a hard link and a symbolic link?

5. What is a mount point?

6. What is the purpose of `/proc`?

7. Why is `/dev/null` useful?

8. What are standard file descriptors?

9. What command displays inode numbers?

10. Why are file metadata and inodes important in digital forensics?

---

# 🎯 Key Takeaways

✅ Linux stores file metadata in inodes.

✅ File names are stored separately from file data.

✅ Hard links share the same inode.

✅ Symbolic links point to file paths.

✅ `/proc`, `/sys`, and `/dev` are special virtual file systems.

✅ File descriptors manage input, output, and error streams.

✅ Understanding Linux internals is essential for cybersecurity, forensics, and system administration.

---

# 📚 Next Lesson

➡ **11 - Linux Command Cheat Sheet & Productivity Tips**

Topics include:

- Frequently Used Commands
- Keyboard Shortcuts
- Bash History Tricks
- Redirection Summary
- File Management Quick Reference
- Networking Commands
- Process Commands
- Permission Commands
- Package Management Commands
- Daily Linux Workflow

---

<div align="center">

## ⭐ "Commands teach you how to use Linux. Understanding the file system teaches you how Linux works."

**Happy Learning! 🐧**

</div>
