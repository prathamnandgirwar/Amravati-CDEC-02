Day 9: Managing Users and Permissions in Linux
Overview of User and Permission Management
User and permission management is essential for securing a Linux system and controlling access to resources. This involves creating, modifying, and managing users, groups, and permissions to ensure proper access control.

Practical:
Identify the current user:
whoami

View all users on the system:
cat /etc/passwd

User Administration:

1. User
 A user is a person who utilizes computer or network services.
 Linux is secured because one user can’t access the files of another user without permission.

2. Types of User

1) Super User
 Super user / Root user
 Those who have root privileges and have access to the entire OS.
Shell used: /bin/bash
UID: 0

2) System User
 Normal user account created during installation.
 System user accounts are created automatically.
Shell used: /sbin/nologin
UID: 1–999
This account has moderate privileges.

3) Standard User
 Also known as local user account.
 This account is used for users who need to work on the server and require limited access.
Shell used: /bin/bash
UID: 1000–60000+

User Related Files:
1.) /etc/passwd 
2.) /etc/shadow 

Group Related Files:
1.) /etc/group  
2.) /etc/gshadow

When a user is created, there are four main user administration related files, along with home directory and skeleton (skel) files.

1.) /etc/passwd (7)
    → It stores user profile–related information.

2.) /etc/shadow (9)
    → It stores user password policies.

3.) /etc/group (4)
    → It stores group-related information for each account.

4.) /etc/gshadow (4)
    → It stores group password and members list.

5.) Home directory & mail account of new user
    → /home/<user_name>  &&  /var/spool/mail

6.) Skeleton files
    → Stored in /etc/skel
    → Files from /etc/skel are copied to the user’s home directory.
    → Skeleton files mean profile files of user.

.bash_logout
→ It executes when the user logs out from the system.

.bash_profile
→ Executes at first-time login in shell.
→ It sources from .bashrc.
→ Used to set aliases and environment variables for the user.

.bashrc
→ This file sources from /etc/bashrc.
→ Used to set aliases.
→ This file is sourced by .bash_profile.

.bash_history
→ Stores command history.
→ File is created after once logout & login.
→ It is NOT copied from /etc/skel while creating a new user account.

Using useradd Command
The useradd command creates new user accounts.

Syntax:
useradd [options] username

Options:
-m: Create a home directory for the user.
-s: Specify the default shell.
-G: Add the user to supplementary groups.

Practical:
Add a new user:
sudo useradd -m -s /bin/bash john

Verify the user:
id john

# su - <user_name>      → To switch the user

Setting User Passwords
Set or change a user password using the passwd command.

Practical:
Set a password for a user:
sudo passwd john

Test login with the new credentials.

/etc/passwd   :- Fields present in this file
1. Username  
2. Linked password  
3. UID  
4. GID  
5. Comment  
6. Home Directory  
7. Shell.

Managing User Groups
Groups simplify permission management by categorizing users.

Commands:
groupadd: Create a new group.
usermod -aG: Add a user to a group.
groups: Display groups a user belongs to.

Practical:
Create a new group:
sudo groupadd developers

Add a user to the group:
sudo usermod -aG developers john

Verify group membership:
groups john
Sudo cat /etc/group | grep developers

Removing Users
Delete a user account using the userdel command.

Practical:
Remove a user:
sudo userdel john

Remove a user and their home directory:
sudo userdel -r john

Introduction to Affected Files
Several system files are affected during user and permission management:

/etc/passwd: Stores user account details.
/etc/shadow: Stores encrypted passwords.
/etc/group: Stores group details.

Practical:
View the contents of /etc/passwd:
cat /etc/passwd

Check group details:
cat /etc/group

User Home Directories
Each user has a dedicated home directory for personal files, typically located in /home/username.

Practical:
View a user’s home directory:
ls /home

Access another user’s home directory (as root):
sudo ls /home/john

Switching Between Users in Linux
Switching users is necessary for testing or administrative tasks.

Using su Command
The su command switches to another user account.

Practical:
Switch to another user:
su john

Return to the previous user:
exit

Using sudo Command
The sudo command allows running commands as another user, typically root.

Practical:
Run a command as root:
sudo apt update

Verify sudo privileges:
sudo -l

🔐 What is the sudoers file?
The sudoers file controls who can run what commands as root (or another user) using sudo.

File location:
/etc/sudoers

Purpose:
Allow selected users/groups to run privileged commands without sharing the root password.
sudoers decides who can become root, for which command, and from where.

Sudoers file format:
user  host=(run_as_user)  command

Example:
labex ALL=(ALL) ALL
user1 ALL=(ALL) NOPASSWD: ALL

Meaning:
labex → user
ALL → from any host
(ALL) → can act as any user (root)
ALL → can run all commands

Example:
useradd -m student1
passwd student1
id student1
su - student1
sudo ls /root

Sudo Visudo
student1 ALL=(ALL) ALL
su - student1
sudo ls /root

Explain to students:
This user is now a sudo admin, almost like root
