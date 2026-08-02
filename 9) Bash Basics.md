<div align="center">

# 🐉 Kali Linux Masterclass
## 📘 Phase 1 – Linux Fundamentals

# 08 - Bash Basics

*"The Bash shell is more than a command interpreter—it's one of the most powerful automation tools in Linux."*

![Linux](https://img.shields.io/badge/Linux-Bash-FCC624?style=for-the-badge&logo=gnu-bash)
![Kali](https://img.shields.io/badge/Kali-Linux-557C94?style=for-the-badge&logo=kalilinux)
![Shell](https://img.shields.io/badge/Shell-Beginner-success?style=for-the-badge)

</div>

---

# 📚 Table of Contents

- Introduction
- What is Bash?
- Why Learn Bash?
- Shell vs Terminal
- Running Commands
- Command History
- Auto Completion
- Command Chaining
- Wildcards
- Aliases
- Variables
- Environment Variables
- Command Substitution
- Basic Bash Scripts
- Best Practices
- Cybersecurity Perspective
- Hands-on Lab
- Cheat Sheet
- Interview Questions
- Key Takeaways

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

✅ Understand the Bash shell

✅ Use command history

✅ Create aliases

✅ Work with shell variables

✅ Use wildcards

✅ Chain commands together

✅ Write simple Bash scripts

---

# 🌟 Introduction

Every time you open a terminal in Kali Linux, you're usually interacting with **Bash (Bourne Again SHell)**.

Bash is a **command-line interpreter**. It reads the commands you type, interprets them, and tells the Linux kernel what to do.

For cybersecurity professionals, Bash is invaluable because it allows repetitive tasks to be automated and multiple commands to be combined into efficient workflows.

---

# 🧠 Shell vs Terminal

Many beginners think these are the same thing, but they are different.

| Terminal | Shell |
|----------|-------|
| A program that displays the command-line interface | The program that interprets your commands |
| Example: GNOME Terminal, Konsole | Example: Bash, Zsh, Fish |

```
Keyboard
    │
    ▼
Terminal
    │
    ▼
Bash Shell
    │
    ▼
Linux Kernel
```

---

# 💡 Why Learn Bash?

Bash helps you:

- Automate repetitive tasks
- Manage files efficiently
- Execute multiple commands quickly
- Write scripts
- Administer Linux systems
- Control cybersecurity tools

Many penetration testing tools are launched or automated using Bash scripts.

---

# ▶ Running Commands

Example:

```bash
pwd
```

Display current directory.

```bash
ls
```

List files.

```bash
date
```

Display current date and time.

```bash
whoami
```

Display current user.

---

# 📜 Command History

Bash remembers previously executed commands.

View history:

```bash
history
```

Example:

```
1 pwd

2 ls

3 cd Documents

4 nano notes.txt
```

---

## Execute a Previous Command

Run command number 15:

```bash
!15
```

Run the last command:

```bash
!!
```

Run the most recent command beginning with "apt":

```bash
!apt
```

---

# ⌨ Auto Completion

Press:

```
TAB
```

Example:

```bash
cd Doc<TAB>
```

Becomes:

```bash
cd Documents
```

Benefits:

- Faster typing
- Fewer mistakes
- Shows possible completions

Double press `TAB` to list multiple matches.

---

# 🔗 Command Chaining

Execute multiple commands in one line.

---

## ;

Runs commands one after another regardless of success.

```bash
pwd ; ls ; date
```

---

## &&

Run the next command **only if** the previous one succeeds.

```bash
mkdir Test && cd Test
```

If `mkdir` fails,

`cd Test` will not execute.

---

## ||

Run the next command **only if** the previous one fails.

```bash
mkdir Test || echo "Folder already exists"
```

---

# ⭐ Wildcards

Wildcards help match multiple files.

---

## *

Matches any number of characters.

```bash
ls *.txt
```

Matches:

```
notes.txt

server.txt

users.txt
```

---

## ?

Matches exactly one character.

```bash
ls file?.txt
```

Matches:

```
file1.txt

fileA.txt
```

Does **not** match:

```
file10.txt
```

---

## []

Match a range or set of characters.

```bash
ls file[1-5].txt
```

Matches:

```
file1.txt

file2.txt

...

file5.txt
```

---

# 🏷 Aliases

Aliases create shortcuts for long commands.

Create:

```bash
alias ll='ls -la'
```

Now:

```bash
ll
```

runs:

```bash
ls -la
```

---

View all aliases:

```bash
alias
```

Remove an alias:

```bash
unalias ll
```

---

# 📦 Shell Variables

Variables temporarily store information.

Create:

```bash
name="Farhan"
```

Display:

```bash
echo $name
```

Output:

```
Farhan
```

Variables only exist in the current shell session unless exported.

---

# 🌍 Environment Variables

Environment variables are available to child processes and affect how programs behave.

Display one:

```bash
echo $HOME
```

Example:

```
/home/farhan
```

Useful environment variables:

| Variable | Purpose |
|-----------|----------|
| `$HOME` | Home directory |
| `$USER` | Current username |
| `$PWD` | Current directory |
| `$PATH` | Command search paths |
| `$SHELL` | Current shell |
| `$HOSTNAME` | System hostname |

View all:

```bash
printenv
```

or

```bash
env
```

---

# 🔄 Command Substitution

Use the output of one command inside another.

Modern syntax:

```bash
echo "Today is $(date)"
```

Example Output:

```
Today is Sun Aug 2 12:00:00 IST 2026
```

Older syntax (still supported):

```bash
echo "Today is `date`"
```

The `$(...)` form is recommended because it is easier to read and nest.

---

# 📜 Basic Bash Script

Create a script:

```bash
nano hello.sh
```

Contents:

```bash
#!/bin/bash

echo "Hello, Linux!"

echo "Welcome to Bash."
```

Save.

Make it executable:

```bash
chmod +x hello.sh
```

Run:

```bash
./hello.sh
```

Output:

```
Hello, Linux!

Welcome to Bash.
```

---

# 🧠 Shebang (`#!`)

The first line of many scripts is:

```bash
#!/bin/bash
```

This tells Linux to execute the script using the Bash interpreter.

---

# 🌍 Real-World Cybersecurity Example

A penetration tester needs to check whether three tools are installed.

Instead of running them one by one:

```bash
which nmap && which sqlmap && which hydra
```

If all commands succeed, the tools are available.

If one fails, the chain stops, making troubleshooting easier.

---

# 🛡 Cybersecurity Perspective

Bash is heavily used for:

- Automation
- Log analysis
- Reconnaissance
- System administration
- Security auditing
- Backup scripts
- Tool orchestration

Understanding Bash makes security tasks faster and more reliable.

---

# ⚠ Common Beginner Mistakes

❌ Forgetting `$` when displaying variables.

```bash
echo name
```

instead of

```bash
echo $name
```

---

❌ Forgetting to make scripts executable.

```bash
chmod +x script.sh
```

---

❌ Using spaces around `=` in variable assignments.

Incorrect:

```bash
name = Farhan
```

Correct:

```bash
name="Farhan"
```

---

❌ Using `;` when `&&` is more appropriate.

---

# 💼 Industry Tip

Professional Linux users rarely type long commands repeatedly.

They rely on:

- Aliases
- History
- Auto-completion
- Bash scripts

These features greatly improve productivity.

---

# 🧪 Hands-on Lab

```bash
history

pwd ; ls

mkdir BashLab && cd BashLab

touch file1.txt file2.txt file3.log

ls *.txt

alias ll='ls -la'

ll

name="Farhan"

echo $name

echo $HOME

echo "Current directory: $PWD"

echo "Today is $(date)"

nano hello.sh

chmod +x hello.sh

./hello.sh
```

---

# 🎯 Mini Challenge

1.

Create an alias named:

```text
update
```

that runs:

```bash
sudo apt update && sudo apt upgrade
```

2.

Create a variable named:

```text
course
```

Store:

```
Cybersecurity
```

Display it.

3.

List only `.txt` files.

4.

Display your home directory.

5.

Create and execute your first Bash script.

---

# 📋 Command Cheat Sheet

| Command | Purpose |
|----------|----------|
| `history` | Show command history |
| `!!` | Repeat last command |
| `!number` | Run command by history number |
| `TAB` | Auto-complete |
| `;` | Run commands sequentially |
| `&&` | Run next command if successful |
| `\|\|` | Run next command if previous fails |
| `*` | Match many characters |
| `?` | Match one character |
| `[]` | Match character range |
| `alias` | Create shortcut |
| `unalias` | Remove alias |
| `echo $VAR` | Display variable |
| `printenv` | Show environment variables |
| `$(command)` | Command substitution |

---

# 🧠 Memory Trick

```
history

Past Commands
```

↓

```
alias

Shortcut
```

↓

```
$

Variable
```

↓

```
&&

If Success
```

↓

```
||

If Failure
```

↓

```
*

Many Files
```

---

# ❓ Interview Questions

1. What is Bash?

2. What is the difference between a shell and a terminal?

3. What is an alias?

4. What is the purpose of environment variables?

5. Explain the difference between `;`, `&&`, and `||`.

6. What is command substitution?

7. Why is `#!/bin/bash` used?

8. What does `$PATH` contain?

9. What is the difference between a shell variable and an environment variable?

10. Why is Bash important in cybersecurity?

---

# 🎯 Key Takeaways

✅ Bash is the default shell on many Linux systems, including most Kali installations.

✅ The shell interprets commands and communicates with the Linux kernel.

✅ Aliases simplify frequently used commands.

✅ Variables store temporary information.

✅ Environment variables influence how programs run.

✅ Wildcards help match multiple files efficiently.

✅ Bash scripts automate repetitive tasks.

---

# 📚 Next Lesson

➡ **09 - Environment Variables**

Topics include:

- What are Environment Variables?
- PATH Variable
- HOME Variable
- USER Variable
- SHELL Variable
- Exporting Variables
- Persistent Variables
- `.bashrc`
- `.profile`
- Security Considerations

---

<div align="center">

## ⭐ "The terminal lets you control Linux. Bash lets you automate it."

**Happy Learning! 🐧**

</div>
