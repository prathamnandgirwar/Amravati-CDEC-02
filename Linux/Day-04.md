# 🐧 Day 4: Mastering the Linux Prompt

![Linux](https://img.shields.io/badge/Linux-CLI-yellow?logo=linux)
![Shell](https://img.shields.io/badge/Bash-Terminal-black?logo=gnubash)
![Level](https://img.shields.io/badge/Level-Beginner-blue)
![Practice](https://img.shields.io/badge/Hands--On-Practice-green)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

# 💻 Understanding the Linux Command Prompt

The Linux command prompt is a powerful interface used to interact with the operating system.

Typical structure: username@hostname:~$

---

## 🔎 Key Components

| Component | Meaning |
|------------|----------|
| username | Current logged-in user |
| hostname | Computer name |
| ~ | Home directory |
| $ | Standard user |
| # | Root user |

---

# 🧠 Decoding the Command Prompt

Understanding prompt elements helps you navigate effectively.

| Symbol/Command | Purpose |
|----------------|----------|
| `~` | User's home directory |
| `pwd` | Show current directory |
| `whoami` | Show current user |
| `hostname` | Show machine name |

---

# 🚀 Effective Command Prompt Usage

## 📂 Navigating Directories

```bash
cd        # Change directory
ls        # List files
pwd       # Print working directory
cd ..     # Go back one directory
cd ~      # Go to home directory

## 📂 Managing Files

touch filename      # Create empty file
mkdir dirname       # Create directory
rm filename         # Delete file

## 📌 Linux Basic Commands

## 1️⃣ Navigation Commands

```bash
pwd
ls
cd /etc
cd ..
cd ~
---

## 2️⃣ File & Directory Commands

```bash
mkdir test
touch file1.txt
ls
rm file1.txt
rmdir test

##  Viewing Files

```bash
cat /etc/os-release

## 📊 Essential System Information Commands

```bash
🖥️ CPU, Memory & Disk
top
free -h
df -h
uptime

## 👤 OS & User Info

```bash
uname -a
whoami
hostname
date

## 🛠️ System Information Commands Explained

```bash
Command	Description

```bash
uname -a	System details
df -h	Disk usage
top	Live process monitoring
free -m	Memory usage
who	Logged-in users


```

## 📂 Creating Files Inside a Directory (from Root)


```bash
touch /home/<username>/<filename>

🔢 Create Multiple Files at Once
touch linux{1..10}.txt


OR

touch linux1.txt linux2.txt

🗑️ Delete All at Once
rm -f linux*

📍 Create Files in Different Locations
touch /mnt/file1.txt /media/file2.txt


Delete forcefully:

rm -f /mnt/file1.txt /media/file2.txt

## 📁 Directory Creation
➤ Create Single Directory in Root
mkdir /dir1

➤ Create Multiple Directories
mkdir /root/{demo,data,practice}
mkdir /session{1..10}

➤ Delete Multiple Directories
rmdir session*

➤ Create Directories in Different Locations
mkdir /root/dir2 /mnt/dir3 /media/dir3

## 🗑️ Deleting Directories with Files Inside
rm -r directory_name

## 🔑 Important Options
Option	Meaning
-r	Recursive delete (includes files inside directory)
-f	Force delete (no confirmation)
-v	Verbose (shows what's happening)

## Example:

rm -rfv directory_name

## 📌 Difference Between rmdir and rm
Command	Works On
rmdir	Empty directories only
rm -r	Directories with files


## 🎯 Summary


```bash

The Linux prompt is a powerful tool for system control.

Understanding the prompt structure improves efficiency.

Mastering file and directory commands is essential.

System monitoring commands help in administration tasks.

Recursive and force options allow advanced deletion operations.


```

---

