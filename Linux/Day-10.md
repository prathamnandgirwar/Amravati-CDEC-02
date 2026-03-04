Managing Users and Permissions in Linux
Day 10: Managing Users and Permissions in Linux

In this lesson, we'll dive deep into user and group management in Linux, including practical applications, commands, and configuration file details.

Importance of Password Security
Passwords are the first line of defense for user accounts. Weak passwords can lead to unauthorized access and compromise system security. Ensure users set complex passwords and follow password policies.

Key Practices:
Use at least 8 characters with a mix of upper/lower case letters, numbers, and special characters.
Periodically change passwords to minimize exposure risk.
Avoid sharing passwords.

Using passwd Command
The passwd command is used to change a user's password and manage password-related settings.

Syntax:
passwd [OPTIONS] [USER]

Examples:
Change the current user’s password:
passwd

Change another user's password (requires root privileges):
passwd username

Lock a user's account:
passwd -l username

Unlock a user's account:
passwd -u username

Expire a user's password to force a reset on the next login:
passwd -e username

How to Verify Account is Locked
Check /etc/shadow
Sudo cat /etc/shadow | grep <username>

Account Locking and Expiration
Locking accounts can prevent unauthorized logins, while expiration ensures unused accounts are deactivated.

Lock Account:
passwd -l username

Check Account Details:
chage -l username

Understanding /etc/shadow Fields
The /etc/shadow file stores encrypted passwords and account metadata.

Fields:
username:password:last_change:min_days:max_days:warn:inactive:expire

username: User login name.
password: Encrypted password (or ! for locked accounts).
last_change: Days since epoch when password last changed.
min_days: Minimum days before a password change is allowed.
max_days: Maximum days before a password must be changed.
warn: Days before expiry to warn the user.
inactive: Days after password expiry before account lock.
expire: Absolute account expiry date.

Using chage Command
The chage command manages password aging and account expiration.

Syntax:
chage [OPTIONS] [USER]

Examples:
View password aging details:
chage -l username

Set maximum password age:
chage -M 90 username

Force password change at next login:
chage -d 0 username

Introduction to Linux Groups
Groups allow multiple users to share permissions and access to resources.

Types of Groups:
Primary Group: Associated with the user by default (specified during user creation).
Secondary Group: Additional groups a user is part of.

Fields of /etc/group and /etc/gshadow

/etc/group:
Contains group information.
group_name:x:GID:members

group_name: Name of the group.
x: Placeholder for password (if any).
GID: Group ID.
members: Comma-separated list of group members.

/etc/gshadow:
Contains secure group passwords and metadata.
group_name:password:admin_users:members

password: Encrypted group password (rarely used).
admin_users: Users allowed to administer the group.
members: Regular group members.

Managing Groups

Creating Groups:
groupadd group_name

Deleting Groups:
groupdel group_name

Modifying Groups:

Change group name:
groupmod -n new_name old_name

Change GID:
groupmod -g new_gid group_name

Managing Group Memberships

Add a User to a Group:
usermod -aG group_name username

Remove a User from a Group:
Edit /etc/group manually or use gpasswd:
gpasswd -d username group_name

View Group Memberships:
groups username

Viewing and Editing Group Information

List All Groups:
cat /etc/group

Practical Examples

Scenario 1: Create a New Team

Create a group:
groupadd dev_team

Add users to the group:
usermod -aG dev_team alice
usermod -aG dev_team bob

Verify membership:
groups alice

By following these practices and using the mentioned commands, you can effectively manage users, passwords, and groups in Linux.
