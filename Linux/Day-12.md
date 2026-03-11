# Day 12: Managing Users and Permissions in Linux

---

# Link Count Basics

## Overview

In Linux, the **link count** refers to the number of references (links) to a particular **inode**.  
An **inode** is a data structure that stores metadata about a file or directory.

---

## Key Points

### Files and Hard Links
- Each file starts with a **link count of 1**
- This represents its **own name as a reference to its inode**

### Directories
Directories typically have a **link count greater than 2** due to:

- `.` → current directory  
- `..` → parent directory  
- Subdirectory entries  

---

# Practical Example

Check the link count of files and directories:

```bash
ls -l
```

Example Output:

```
drwxr-xr-x  2 user group 4096 Dec 18 10:00 example-dir
-rw-r--r--  1 user group   45 Dec 18 10:00 example-file
```

### Explanation

- Directory **example-dir** has a link count of **2**
- File **example-file** has a link count of **1**

---

# Link Count for Directories

### Base Count

A directory always starts with at least **two links**:

- `.` → itself  
- `..` → parent directory  

### Subdirectories

Each subdirectory **increases the parent directory’s link count by 1**

---

## Example

```bash
mkdir dir1
mkdir dir1/subdir1
ls -ld dir1
```

Output:

```
drwxr-xr-x 3 user group 4096 Dec 18 10:00 dir1
```

Explanation:

`dir1` has **three links**

- `.`
- `..`
- `subdir1`

---

# Comparing Hard and Soft Links

## Hard Links

- Point to the **same inode**
- Cannot span across **different file systems**
- Cannot link to **directories**

---

## Soft Links (Symbolic Links)

- Act as a **pointer to the original file**
- Can span across **file systems**
- Can link to **directories**

---

# Practical Example

### Hard Link

```bash
ln original hardlink
ls -li
```

### Soft Link

```bash
ln -s original softlink
ls -li
```

---

# What is a Hard Link?

A **hard link** is another name for the **same file**, pointing to the **same inode**.

---

## Step 1: Create a File

```bash
echo "Hello Linux" > file1.txt
```

Check inode:

```bash
ls -li file1.txt
```

---

## Step 2: Create Hard Link

```bash
ln file1.txt file1_hard.txt
```

Check again:

```bash
ls -li file1.txt file1_hard.txt
```

### Observation

- Same **inode number**
- Link count increases to **2**
- Both files contain **same data**

---

## Step 3: Modify File

```bash
echo "Hard link test" >> file1_hard.txt
cat file1.txt
```

Changes will appear in **both files**

---

## Step 4: Delete Original File

```bash
rm file1.txt
ls -l file1_hard.txt
```

Result:

- File **still exists**
- Data is **safe**

---

## Hard Link Summary

- Works only for **files**
- Same **inode**
- Data survives even if **original file is deleted**

---

# What is a Soft Link?

A **soft link (symbolic link)** is a **shortcut** that stores the **path of the original file or directory**.

---

## Step 1: Create a File

```bash
echo "Hello Soft Link" > file2.txt
```

Check:

```bash
ls -li file2.txt
```

---

## Step 2: Create Soft Link

```bash
ln -s file2.txt file2_soft.txt
```

Check:

```bash
ls -li file2.txt file2_soft.txt
```

### Observation

- Different **inode numbers**
- Link count **unchanged**
- File type = **l** (symbolic link)

---

## Step 3: Access via Soft Link

```bash
cat file2_soft.txt
```

Data is accessible.

---

## Step 4: Delete Original File

```bash
rm file2.txt
cat file2_soft.txt
```

Error:

```
No such file or directory
```

The **soft link becomes broken**.

---

# Soft Link for Directory (Important)

```bash
mkdir dir1
ln -s dir1 dir1_soft
ls -ld dir1 dir1_soft
```

Observation:

- Soft link works for **directories**
- Hard link **does NOT work for directories**

---

# Hard Link vs Soft Link

| Feature | Hard Link | Soft Link |
|------|------|------|
| Command | `ln` | `ln -s` |
| File type | `-` | `l` |
| Works for directories | ❌ | ✅ |
| Inode | Same | Different |
| Link count | Increases | No change |
| Delete original file | Safe | Link breaks |

---

# chown Command (Change Owner)

## What is chown?

`chown` is used to **change the user owner and/or group owner** of a file or directory.

---

## Syntax

```bash
chown <owner_name>:<group_name> file_or_directory
```

---

## Examples

### Change User and Group

```bash
chown chetan:devops file1.txt
```

Owner → **chetan**  
Group → **devops**

---

### Change Only User

```bash
chown chetan file1.txt
```

---

### Change Only Group

```bash
chown :devops file1.txt
```

---

# Who Can Use chown?

Only **root or sudo users** can change file ownership.

Reason: Ownership control is a **security-critical operation**.

---

# Importance of sudo for Privilege Escalation

## What is sudo?

`sudo` allows a permitted user to **execute commands as another user**, typically **root**.

It provides **controlled privilege escalation**.

---

## Why Use sudo?

- Prevent accidental **system damage**
- Provide **audit trail of user activities**
- Allow **specific command permissions**

---

## Example

Run a privileged command:

```bash
sudo apt update
```

---

# Regular Command vs sudo Command

Regular command:

```bash
ls /root
```

Output:

```
Permission denied
```

Using sudo:

```bash
sudo ls /root
```

Now you can access the **/root directory**.

---

# Configuring sudo Access

## Edit sudoers File

Use the **visudo** command:

```bash
sudo visudo
```

This safely edits:

```
/etc/sudoers
```

---

## Grant User Permissions

```
username ALL=(ALL) ALL
```

---

## Restrict Commands

Allow a user to run only specific commands:

```
username ALL=(ALL) NOPASSWD: /sbin/reboot
```

---

# Example: Add User to sudo Group

```bash
sudo usermod -aG sudo username
```

This grants the user **sudo privileges**.
