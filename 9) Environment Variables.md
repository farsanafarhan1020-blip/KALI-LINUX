<div align="center">

# 🐉 Kali Linux Masterclass
## 📘 Phase 1 – Linux Fundamentals

# 09 - Environment Variables

*"Environment variables silently guide how Linux and its programs behave."*

![Linux](https://img.shields.io/badge/Linux-Environment%20Variables-FCC624?style=for-the-badge&logo=linux)
![Kali](https://img.shields.io/badge/Kali-Linux-557C94?style=for-the-badge&logo=kalilinux)
![Shell](https://img.shields.io/badge/Bash-Environment-success?style=for-the-badge)

</div>

---

# 📚 Table of Contents

- Introduction
- What are Environment Variables?
- Shell Variables vs Environment Variables
- Viewing Variables
- Common Environment Variables
- Creating Variables
- Exporting Variables
- PATH Variable
- Making Variables Persistent
- .bashrc & .profile
- Security Best Practices
- Cybersecurity Perspective
- Hands-on Lab
- Cheat Sheet
- Interview Questions
- Key Takeaways

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

✅ Understand environment variables

✅ View existing variables

✅ Create your own variables

✅ Export variables

✅ Modify the PATH variable

✅ Make variables permanent

---

# 🌟 Introduction

Every Linux program runs inside an **environment**.

This environment contains useful information such as:

- Current user
- Home directory
- Terminal type
- Current shell
- Language
- Command search paths

This information is stored in **environment variables**.

Think of them as small pieces of information that programs can access whenever they need them.

---

# 🧠 What is an Environment Variable?

An **environment variable** is a named value that stores information used by the shell and other programs.

Example:

```
HOME=/home/farhan
```

Here:

```
Variable Name

↓

HOME

Variable Value

↓

/home/farhan
```

Applications can read these values to determine how they should behave.

---

# 📦 Shell Variables vs Environment Variables

| Shell Variable | Environment Variable |
|----------------|----------------------|
| Exists only in the current shell | Passed to child processes |
| Private to the shell | Available to programs launched from the shell |
| Created normally | Created using `export` |

Example:

```bash
course="Cybersecurity"
```

Only the current shell knows about it.

Now export it:

```bash
export course
```

Any program started after this can access it.

---

# 👀 Viewing Variables

Display a specific variable:

```bash
echo $HOME
```

Display the current user:

```bash
echo $USER
```

Display the current shell:

```bash
echo $SHELL
```

Display all environment variables:

```bash
printenv
```

or

```bash
env
```

---

# 🌍 Common Environment Variables

| Variable | Description |
|-----------|-------------|
| `$HOME` | Home directory |
| `$USER` | Current username |
| `$PWD` | Present working directory |
| `$OLDPWD` | Previous working directory |
| `$PATH` | Command search locations |
| `$SHELL` | Current shell |
| `$HOSTNAME` | Computer name |
| `$LANG` | Language settings |
| `$TERM` | Terminal type |

---

# 🔧 Creating a Shell Variable

Create:

```bash
course="Cybersecurity"
```

Display:

```bash
echo $course
```

Output:

```
Cybersecurity
```

This variable exists only until the shell is closed.

---

# 🚀 Exporting a Variable

Export a variable:

```bash
export course
```

Or create and export in one step:

```bash
export lab="Kali Linux"
```

Verify:

```bash
printenv lab
```

Output:

```
Kali Linux
```

---

# 🛣 Understanding the PATH Variable

One of the most important environment variables is:

```bash
PATH
```

Display it:

```bash
echo $PATH
```

Example:

```text
/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
```

Each directory is separated by a colon (`:`).

---

## How PATH Works

Suppose you type:

```bash
ls
```

Linux searches for `ls` in each directory listed in `$PATH`.

```
Type:

ls

↓

Search

/usr/local/bin

↓

Not Found

↓

/usr/bin

↓

Found!

↓

Execute
```

Without `PATH`, you would need to type the full path:

```bash
/usr/bin/ls
```

---

# ➕ Temporarily Modify PATH

Add a directory for the current session:

```bash
export PATH=$PATH:/home/farhan/scripts
```

Verify:

```bash
echo $PATH
```

The change disappears when the shell session ends.

---

# 💾 Making Variables Persistent

Temporary variables disappear after logout.

To keep them permanently, add them to your shell configuration file.

Common files:

```
~/.bashrc

~/.profile
```

---

# 📄 .bashrc

The `.bashrc` file runs whenever a new interactive Bash shell starts.

Example:

```bash
nano ~/.bashrc
```

Add:

```bash
export COURSE="Cybersecurity"
```

Save the file.

Apply changes without restarting:

```bash
source ~/.bashrc
```

Verify:

```bash
echo $COURSE
```

---

# 📄 .profile

`.profile` is executed when you log in.

It is commonly used to configure login session settings.

Some Linux distributions use `.profile`, while others may use `.bash_profile` or `.bash_login`.

---

# 🔄 source

The `source` command reloads a configuration file without opening a new terminal.

Example:

```bash
source ~/.bashrc
```

This immediately applies any changes made to `.bashrc`.

---

# 🌍 Real-World Cybersecurity Example

Suppose you frequently use your own security scripts.

Instead of typing:

```bash
/home/farhan/scripts/recon.sh
```

every time,

add the directory to `PATH`:

```bash
export PATH=$PATH:/home/farhan/scripts
```

Now you can simply run:

```bash
recon.sh
```

This saves time and simplifies automation.

---

# 🛡 Cybersecurity Perspective

Environment variables can contain sensitive information such as:

- API tokens
- Database credentials
- Cloud access keys
- Proxy settings

If an attacker gains access to these variables, they may obtain valuable secrets.

Always avoid storing sensitive data in plain text environment variables on shared or production systems unless appropriate security measures are in place.

---

# ⚠ Common Beginner Mistakes

❌ Forgetting the `$` when displaying a variable.

Incorrect:

```bash
echo HOME
```

Correct:

```bash
echo $HOME
```

---

❌ Overwriting the `PATH` variable.

Incorrect:

```bash
export PATH=/home/farhan/scripts
```

This removes all existing search paths.

Correct:

```bash
export PATH=$PATH:/home/farhan/scripts
```

---

❌ Editing `.bashrc` but forgetting to reload it.

Use:

```bash
source ~/.bashrc
```

---

# 💼 Industry Tip

System administrators often use environment variables to:

- Configure development tools
- Store software locations
- Define programming language paths
- Customize the shell
- Simplify daily workflows

---

# 🧪 Hands-on Lab

```bash
echo $HOME

echo $USER

echo $PWD

echo $PATH

course="Cybersecurity"

echo $course

export course

printenv course

export LAB="Linux"

echo $LAB

nano ~/.bashrc

source ~/.bashrc
```

---

# 🎯 Mini Challenge

1.

Display your:

- Home directory
- Username
- Shell
- PATH

2.

Create:

```bash
mentor="ChatGPT"
```

3.

Export it.

4.

Verify it using:

```bash
printenv mentor
```

5.

Add a custom directory to `PATH` temporarily.

6.

Reload `.bashrc` using `source`.

---

# 📋 Command Cheat Sheet

| Command | Purpose |
|----------|----------|
| `echo $VAR` | Display variable |
| `printenv` | Show environment variables |
| `env` | Display environment |
| `export` | Export variable |
| `echo $PATH` | Display PATH |
| `source ~/.bashrc` | Reload Bash configuration |
| `nano ~/.bashrc` | Edit Bash configuration |

---

# 🧠 Memory Trick

```
HOME

My Home Folder
```

↓

```
USER

Who Am I?
```

↓

```
PWD

Where Am I?
```

↓

```
PATH

Where Linux Searches
```

↓

```
export

Share Variable
```

↓

```
source

Reload Configuration
```

---

# ❓ Interview Questions

1. What is an environment variable?

2. What is the difference between a shell variable and an environment variable?

3. What is the purpose of the `PATH` variable?

4. Why is `export` used?

5. What is `.bashrc`?

6. What does the `source` command do?

7. Why should you avoid overwriting `PATH`?

8. Name five common environment variables.

9. Where are environment variables commonly stored?

10. Why are environment variables important in Linux?

---

# 🎯 Key Takeaways

✅ Environment variables store information used by the shell and programs.

✅ `export` makes variables available to child processes.

✅ `PATH` tells Linux where to search for executable programs.

✅ `.bashrc` is commonly used to store persistent Bash settings.

✅ `source` reloads configuration files without opening a new shell.

✅ Proper management of environment variables improves productivity and security.

---

# 📚 Next Lesson

➡ **10 - Linux File System Deep Dive**

Topics include:

- Inodes
- Hard Links
- Symbolic Links
- Mount Points
- File Descriptors
- `/proc`
- `/sys`
- `/dev`
- Virtual File Systems
- Disk Layout
- How Linux Stores Files Internally

---

<div align="center">

## ⭐ "Environment variables may be invisible, but they shape how every Linux program runs."

**Happy Learning! 🐧**

</div>
