<div align="center">

# 🐉 Kali Linux Masterclass
## 📘 Phase 1 – Linux Fundamentals

# 03 - Working with Files & Text

*"Data is everywhere. Linux gives you the power to create it, edit it, search it, and analyze it efficiently."*

![Linux](https://img.shields.io/badge/Linux-Files-blue?style=for-the-badge&logo=linux)
![Kali](https://img.shields.io/badge/Kali-Linux-557C94?style=for-the-badge&logo=kalilinux)
![Level](https://img.shields.io/badge/Level-Beginner-success?style=for-the-badge)

</div>

---

# 📚 Table of Contents

- Introduction
- Understanding Text Files
- echo
- cat
- nano
- less
- head
- tail
- wc
- grep
- Redirection
- Pipes
- Real World Examples
- Hands-on Lab
- Cheat Sheet
- Interview Questions
- Key Takeaways

---

# 🎯 Learning Objectives

After completing this lesson you will be able to:

✅ Create text files

✅ Write data into files

✅ Read files

✅ Edit files

✅ Search inside files

✅ Count lines, words and characters

✅ Redirect command output

✅ Combine commands using pipes

---

# 🌟 Introduction

Almost everything in Linux is stored as **text**.

Configuration files

Logs

Scripts

User information

Application settings

Server logs

Firewall rules

Understanding how to work with text files is one of the most valuable Linux skills.

---

# 📄 Understanding Text Files

A text file stores readable characters instead of images or binary data.

Examples:

```
notes.txt

server.log

users.txt

config.conf

passwd
```

Most Linux configuration files are plain text.

---

# 📢 echo

## 📖 What is it?

Displays text or writes text into a file.

---

## Syntax

```bash
echo "Hello"
```

---

## Example

```bash
echo "Linux Basics"
```

Output

```
Linux Basics
```

---

## Write to a File

```bash
echo "Linux Basics" > notes.txt
```

Creates the file if it does not exist.

If it already exists,

its contents will be replaced.

---

## Append to a File

```bash
echo "Cyber Security" >> notes.txt
```

Adds the new line without deleting existing data.

---

## Internal Working

The shell passes the text to the `echo` command, which prints it to **standard output (stdout)**. When you use `>` or `>>`, the shell redirects that output into a file instead of displaying it on the screen.

---

## Cybersecurity Importance

Used to:

- Create scripts

- Generate test files

- Write configuration values

- Simulate log entries

---

# 📖 cat

## What is it?

Displays the contents of a file.

---

## Syntax

```bash
cat notes.txt
```

---

## Example

```
Linux Basics

Cyber Security
```

---

## Display Multiple Files

```bash
cat file1.txt file2.txt
```

---

## Create a File

```bash
cat > message.txt
```

Type your text.

Press

```
Ctrl + D
```

to save.

---

## Internal Working

`cat` reads the file sequentially and sends its contents to standard output.

---

## Cybersecurity Importance

Used for:

- Viewing logs

- Reading configuration files

- Verifying output

---

# ✏ nano

## What is it?

A beginner-friendly text editor.

---

## Open a File

```bash
nano notes.txt
```

---

## Save

```
Ctrl + O
```

---

## Exit

```
Ctrl + X
```

---

## Why Nano?

Easy to learn

Available on most Linux systems

Perfect for beginners

---

# 📄 less

## What is it?

Displays large files one page at a time.

Unlike `cat`, it doesn't flood your terminal with thousands of lines.

---

## Syntax

```bash
less logfile.txt
```

---

## Navigation

```
↑ ↓

Space

b

/

n

q
```

| Key | Function |
|------|----------|
| ↑ ↓ | Move line by line |
| Space | Next page |
| b | Previous page |
| /text | Search |
| n | Next match |
| q | Quit |

---

## Cybersecurity Importance

Very useful for viewing:

- Authentication logs

- Web server logs

- Huge configuration files

---

# 📑 head

Displays the first 10 lines.

```bash
head file.txt
```

---

## First 5 Lines

```bash
head -5 file.txt
```

---

# 📑 tail

Displays the last 10 lines.

```bash
tail file.txt
```

---

## Last 3 Lines

```bash
tail -3 file.txt
```

---

## Live Monitoring

```bash
tail -f logfile.log
```

The terminal updates automatically as new lines are written.

Press

```
Ctrl + C
```

to stop.

---

## Cybersecurity Importance

Security analysts frequently monitor:

- Authentication logs

- Firewall logs

- Web server logs

- IDS alerts

using

```bash
tail -f
```

---

# 🔢 wc

## What is it?

Counts:

- Lines

- Words

- Characters

---

## Syntax

```bash
wc notes.txt
```

Example

```
3 10 65 notes.txt
```

Meaning:

```
3 Lines

10 Words

65 Characters/Bytes
```

---

## Useful Options

```bash
wc -l file.txt
```

Only lines

---

```bash
wc -w file.txt
```

Only words

---

```bash
wc -c file.txt
```

Only bytes

---

# 🔍 grep

## What is it?

Searches for text inside files.

---

## Syntax

```bash
grep "Linux" notes.txt
```

---

## Ignore Case

```bash
grep -i "linux" notes.txt
```

Matches

```
Linux

LINUX

linux
```

---

## Line Numbers

```bash
grep -n "Linux" notes.txt
```

---

## Internal Working

`grep` scans each line and compares it with the search pattern. Matching lines are printed to the terminal.

---

## Cybersecurity Importance

Used constantly for:

- Searching logs

- Finding failed logins

- Looking for usernames

- Detecting suspicious activity

---

# 🔄 Redirection

Linux can redirect output.

---

## Overwrite

```bash
>
```

Example

```bash
echo "Hello" > test.txt
```

Old contents are deleted.

---

## Append

```bash
>>
```

Example

```bash
echo "World" >> test.txt
```

Adds to the end.

---

# 🔗 Pipes

A pipe sends the output of one command into another.

```
Command A

↓

|

↓

Command B
```

Example

```bash
history | grep nano
```

The output of `history` becomes the input for `grep`.

---

## Another Example

```bash
grep "Login" server.log | wc -l
```

Flow:

```
server.log

↓

grep

↓

Matching Lines

↓

wc -l

↓

Count
```

---

# 🌍 Real-World Cybersecurity Example

Suppose you receive a server log with 500,000 lines.

Find failed logins:

```bash
grep "Failed" auth.log
```

Count them:

```bash
grep "Failed" auth.log | wc -l
```

Monitor new entries:

```bash
tail -f auth.log
```

View the file comfortably:

```bash
less auth.log
```

This workflow is common in Security Operations Centers (SOCs).

---

# ⚠ Common Beginner Mistakes

❌ Using `>` instead of `>>`

❌ Forgetting Linux is case-sensitive

❌ Trying to read huge files with `cat`

❌ Closing Nano without saving

❌ Forgetting `Ctrl + D` after using `cat > file`

---

# 💼 Industry Tip

Experienced Linux users rarely read large logs with `cat`.

Instead they use:

- less

- grep

- head

- tail

These tools are faster and more practical.

---

# 🧪 Hands-on Lab

```bash
mkdir Lesson3

cd Lesson3

echo "Linux Basics" > notes.txt

echo "Kali Linux" >> notes.txt

echo "Cyber Security" >> notes.txt

cat notes.txt

nano notes.txt

head notes.txt

tail notes.txt

wc notes.txt

grep "Linux" notes.txt

history | grep nano
```

---

# 🎯 Mini Challenge

Create:

```
server.log
```

Add

```
Login Success

Login Failed

Admin Login

Login Failed

Server Started
```

Now answer:

Show only failed logins.

```
grep "Failed" server.log
```

Count login entries.

```
grep "Login" server.log | wc -l
```

Show first three lines.

```
head -3 server.log
```

Show last two lines.

```
tail -2 server.log
```

---

# 📋 Command Cheat Sheet

| Command | Purpose |
|----------|---------|
| echo | Print or write text |
| cat | Display file contents |
| nano | Edit files |
| less | Read large files |
| head | First lines |
| tail | Last lines |
| tail -f | Live monitoring |
| wc | Count |
| grep | Search |
| > | Overwrite |
| >> | Append |
| \| | Pipe output |

---

# ❓ Interview Questions

1. What is the difference between `cat` and `less`?

2. What is the purpose of `grep`?

3. Explain the difference between `>` and `>>`.

4. Why is `tail -f` useful?

5. What does `wc -l` display?

6. What is a pipe?

7. Why is `grep` heavily used in cybersecurity?

---

# 🎯 Key Takeaways

✅ Linux stores most configuration and log data as plain text.

✅ `echo` creates and writes data.

✅ `cat` displays files.

✅ `nano` edits files.

✅ `less` is best for large files.

✅ `head` and `tail` quickly inspect files.

✅ `grep` is the primary search tool in Linux.

✅ Pipes allow commands to work together.

---

# 📚 Next Lesson

➡ **04 - Linux Permissions, Users & Ownership**

Topics include:

- File Permissions
- Read, Write and Execute
- chmod
- chown
- Groups
- Root User
- Numeric Permissions (755, 644, 777)
- Security Best Practices

---

<div align="center">

## ⭐ "In Linux, data is everywhere. Master text processing, and you master the operating system."

**Happy Learning! 🐧**

</div>
