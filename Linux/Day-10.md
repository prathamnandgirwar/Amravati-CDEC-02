# Day 10: Managing Users and Permissions in Linux

## Managing Users and Permissions in Linux

In this lesson, we'll dive deep into user and group management in Linux, including practical applications, commands, and configuration file details.

---

## Importance of Password Security

Passwords are the first line of defense for user accounts. Weak passwords can lead to unauthorized access and compromise system security.

### Key Practices
- Use at least 8 characters with a mix of upper/lower case letters, numbers, and special characters
- Periodically change passwords to minimize exposure risk
- Avoid sharing passwords

---

## Using passwd Command

The `passwd` command is used to change a user's password and manage password-related settings.

### Syntax
```bash
passwd [OPTIONS] [USER]
```

### Examples

Change the current user’s password:
```bash
passwd
```

Change another user's password (requires root privileges):
```bash
passwd username
```

Lock a user's account:
```bash
passwd -l username
```

Unlock a user's account:
```bash
passwd -u username
```

Expire a user's password to force reset on next login:
```bash
passwd -e username
```

---

## How to Verify Account is Locked

Check `/etc/shadow`
```bash
sudo cat /etc/shadow | grep <username>
```

---

## Account Locking and Expiration

Locking accounts prevents unauthorized logins, while expiration ensures unused accounts are deactivated.

Lock account:
```bash
passwd -l username
```

Check account details:
```bash
chage -l username
```

---

## Understanding /etc/shadow Fields

The `/etc/shadow` file stores encrypted passwords and account metadata.

### Format
```
username:password:last_change:min_days:max_days:warn:inactive:expire
```

### Field Explanation
- `username` → User login name
- `password` → Encrypted password (`!` means locked)
- `last_change` → Days since epoch when password last changed
- `min_days` → Minimum days before password can be changed
- `max_days` → Maximum days password is valid
- `warn` → Warning days before expiry
- `inactive` → Days after expiry before account lock
- `expire` → Absolute account expiration date

---

## Using chage Command

The `chage` command manages password aging and account expiration.

### Syntax
```bash
chage [OPTIONS] [USER]
```

### Examples

View password aging details:
```bash
chage -l username
```

Set maximum password age:
```bash
chage -M 90 username
```

Force password change at next login:
```bash
chage -d 0 username
```

---

## Introduction to Linux Groups

Groups allow multiple users to share permissions and access to resources.

### Types of Groups
- **Primary Group** → Default group assigned to user
- **Secondary Group** → Additional groups user belongs to

---

## Fields of /etc/group and /etc/gshadow

### /etc/group
Contains group information.

Format:
```
group_name:x:GID:members
```

- `group_name` → Name of the group
- `x` → Password placeholder
- `GID` → Group ID
- `members` → Comma-separated users

---

### /etc/gshadow
Contains secure group information.

Format:
```
group_name:password:admin_users:members
```

- `password` → Encrypted group password (rarely used)
- `admin_users` → Group administrators
- `members` → Regular members

---

## Managing Groups

Create a group:
```bash
groupadd group_name
```

Delete a group:
```bash
groupdel group_name
```

Modify group name:
```bash
groupmod -n new_name old_name
```

Modify group GID:
```bash
groupmod -g new_gid group_name
```

---

## Managing Group Memberships

Add user to a group:
```bash
usermod -aG group_name username
```

Remove user from a group:
```bash
gpasswd -d username group_name
```

View group membership:
```bash
groups username
```

---

## Viewing Group Information

List all groups:
```bash
cat /etc/group
```

---

## Practical Example

### Scenario: Create a New Team

Create a group:
```bash
groupadd dev_team
```

Add users to the group:
```bash
usermod -aG dev_team alice
usermod -aG dev_team bob
```

Verify membership:
```bash
groups alice
```

---

By following these practices and using the above commands, you can effectively manage users, passwords, and groups in Linux.
