# Day 9: Managing Users and Permissions in Linux

## Overview of User and Permission Management
User and permission management is essential for securing a Linux system and controlling access to resources. This involves creating, modifying, and managing users, groups, and permissions to ensure proper access control.

## Practical
Identify the current user
```bash
whoami
```

View all users on the system
```bash
cat /etc/passwd
```

## User Administration

### 1. User
A user is a person who utilizes computer or network services.  
Linux is secured because one user can’t access the files of another user without permission.

### 2. Types of Users

#### 1) Super User (Root User)
Has root privileges and full access to the OS  
Shell used: /bin/bash  
UID: 0  

#### 2) System User
Created automatically during installation  
Used by system services  
Shell used: /sbin/nologin  
UID: 1–999  
Has moderate privileges  

#### 3) Standard User
Also known as local user  
Used for day-to-day server work  
Limited privileges  
Shell used: /bin/bash  
UID: 1000–60000+  

## User Related Files
/etc/passwd  
/etc/shadow  

## Group Related Files
/etc/group  
/etc/gshadow  

## Files Created When a User Is Created

/etc/passwd (7 fields)  
→ Stores user profile information  

/etc/shadow (9 fields)  
→ Stores encrypted passwords and password policies  

/etc/group (4 fields)  
→ Stores group-related information  

/etc/gshadow (4 fields)  
→ Stores group passwords and members list  

Home directory & mail account  
→ /home/<username> and /var/spool/mail  

Skeleton files  
→ Stored in /etc/skel  
→ Copied to user’s home directory  
→ Default profile files  

## Skeleton Files Explanation

.bash_logout  
Executes when user logs out  

.bash_profile  
Executes at first login  
Sources .bashrc  
Used for environment variables and aliases  

.bashrc  
Sources /etc/bashrc  
Used for aliases  
Loaded for every shell  

.bash_history  
Stores command history  
Created after logout & login  
NOT copied from /etc/skel  

## Using useradd Command

Syntax
```bash
useradd [options] username
```

Options  
-m → Create home directory  
-s → Specify shell  
-G → Add to supplementary groups  

Practical: Add User
```bash
sudo useradd -m -s /bin/bash john
```

Verify User
```bash
id john
```

Switch User
```bash
su - john
```

## Setting User Password
```bash
sudo passwd john
```

## /etc/passwd Fields
Username  
Linked password  
UID  
GID  
Comment  
Home directory  
Shell  

## Managing User Groups

Commands  
groupadd → Create group  
usermod -aG → Add user to group  
groups → Show groups  

Practical
```bash
sudo groupadd developers
sudo usermod -aG developers john
groups john
cat /etc/group | grep developers
```

## Removing Users

Remove User
```bash
sudo userdel john
```

Remove User with Home Directory
```bash
sudo userdel -r john
```

## Affected System Files
/etc/passwd → User details  
/etc/shadow → Passwords  
/etc/group → Group details  

Practical
```bash
cat /etc/passwd
cat /etc/group
```

## User Home Directories
```bash
ls /home
sudo ls /home/john
```

## Switching Between Users

Using su
```bash
su john
exit
```

Using sudo
```bash
sudo apt update
sudo -l
```

## sudoers File

Location  
/etc/sudoers  

Purpose  
Controls who can run commands as root  
Avoids sharing root password  
Defines who, what, and from where  

Format  
user host=(run_as_user) command  

Examples  
labex ALL=(ALL) ALL  
user1 ALL=(ALL) NOPASSWD: ALL  

Meaning  
labex → user  
ALL → any host  
(ALL) → any user (root)  
ALL → all commands  

sudo Demo
```bash
useradd -m student1
passwd student1
id student1
su - student1
sudo ls /root
```

visudo Entry  
student1 ALL=(ALL) ALL  

Explanation for Students  
This user is now a sudo admin, almost like the root user.
