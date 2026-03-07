# Day 14: Automation and Data Handling in Linux

## Overview of Archiving

Archiving is the process of **combining multiple files and directories into a single file**.  
This is especially useful for **backups, data transfer, and organization**.

---

# 1. Archiving

Archiving is the process of combining multiple files/directories into one file.

### Use Cases
- Server Backup
- Moving data from one server to another server

### Command
`tar`

### Syntax
```bash
tar <options> <compressed_file_name>.tar <file_name_to_be_archived>
```

### Important Options

| Option | Meaning |
|------|------|
| `-c` | Create an archive |
| `-f` | File name (compulsory option) |
| `-v` | Verbose (show progress/output) |
| `-t` | List contents of archive |
| `-x` | Extract contents from archive |
| `-C` | Extract archive to another directory |

---

# Example: Backup of `/etc` Directory

Suppose we want to take a backup of the `/etc` directory.

First check the size of the directory.

```bash
du -sh /etc
```

Example Output

```
100MB
```

If the directory size is large, it becomes difficult to store or transfer.  
So we create a **tar archive**.

### Create Archive

```bash
tar -cvf /mnt/etc_bkp.tar /etc
```

### Check Archive Size

```bash
du -sh /mnt/etc_bkp.tar
```

---

## Listing Archive Content

```bash
tar -tvf /etc_bkp.tar | less
```

---

## Extract Archive

### Extract in Current Directory

```bash
tar -xvf etc_bkp.tar
```

### Extract in Another Directory

```bash
tar -xvf etc_bkp.tar -C /media/etc
```

---

# 2. Compression

Compression is the process of **reducing the size of files or directories**.

It reduces the **number of bits needed to represent data**.

### Benefits
- Saves storage space
- Faster file transfer
- Lower storage cost

---

# Compression Methods

| No | Name | Option | Extension |
|---|---|---|---|
| 1 | gzip | `-z` | `.tar.gz` |
| 2 | bzip2 | `-j` | `.tar.bz2` |
| 3 | xz | `-J` | `.tar.xz` |

---

# Compression Comparison

| Tool | Compression | Speed | CPU Usage | Best Use Case |
|-----|-----|-----|-----|-----|
| gzip | Low–Medium | Fast | Low | Logs, daily backups |
| bzip2 | Medium | Slow | Medium | Long-term storage |
| xz | High (Best) | Slowest | High | Archival |

---

# Gzip Compression

```bash
du -sh /etc
tar -cvzf /mnt/etc_bkp.tar.gz /etc
du -sh /mnt/etc_bkp.tar.gz
```

---

# Bzip2 Compression

```bash
tar -cvjf /mnt/etc_bkp.tar.bz2 /etc
du -sh /mnt/etc_bkp.tar.bz2
```

---

# XZ Compression

```bash
tar -cvJf /mnt/etc_bkp.tar.xz /etc
du -sh /mnt/etc_bkp.tar.xz
```

---

# Extraction Using Tar

### Gzip Extraction

```bash
tar -xvzf /mnt/etc_bkp.tar.gz -C /media
```

### Bzip2 Extraction

```bash
tar -xvjf /mnt/etc_bkp.tar.bz2 -C /media
```

### XZ Extraction

```bash
tar -xvJf /mnt/etc_bkp.tar.xz -C /media
```

---

# 3. Job Scheduling

Job Scheduling is the process of **automatically running tasks at a specific time or interval without manual interaction**.

In Linux, it is used for tasks such as:

- Automated backups
- System maintenance
- Scheduled scripts

---

# Cron Jobs

A **cron job** is a scheduled task that allows you to run scripts or commands at specific intervals.

### Why Use Cron Jobs?

- Automated backups
- Automated disk cleaning
- Running scripts periodically
- Scheduled system tasks

---

# Cron Fields

| Field | Range |
|------|------|
| Minute | 0 – 59 |
| Hour | 0 – 23 |
| Day of Month | 1 – 31 |
| Month | 1 – 12 |
| Day of Week | 0 – 6 (Sunday = 0 or 7) |
| Action | Command to execute |

Example Command

```
touch file301.txt
```

---

# Special Symbols

| Symbol | Meaning | Example |
|------|------|------|
| `*` | Every value | every day |
| `-` | Range | 1-5 |
| `/` | Interval | */5 (every 5 minutes) |
| `,` | Multiple values | mon,wed |

---

# Crontab Syntax

```bash
crontab <options>
```

### Options

| Option | Meaning |
|------|------|
| `-e` | Edit crontab |
| `-l` | List crontab |
| `-r` | Remove crontab |
| `-u` | For specific user |

Examples:

```bash
crontab -e -u username
crontab -l -u username
crontab -r -u username
```

---

# Cron Job Examples

### Run Every Minute

```
* * * * * touch file301.txt
```

Creates a file every minute.

---

### Run at Specific Minute

```
5 * * * * touch file301.txt
```

Runs at the **5th minute of every hour**.

---

### Run Every 5 Minutes

```
*/5 * * * * touch file301.txt
```

Runs every **5 minutes**.

---

### Run at Specific Time

```
50 21 10 8 4 touch /media/cedc_b16
```

Runs at **9:50 PM on 10th August if it is Thursday**.

---

### Run Every Minute (Absolute Path)

```
* * * * * /bin/mkdir -p /home/ubuntu/pratham/abc
```

Creates directory **abc** every minute.

---

### Run Every Minute with Unique Name

```
* * * * * /bin/mkdir -p /home/ubuntu/pratham/abc_$(date +\%Y\%m\%d_\%H\%M)
```

Creates a directory with **date & time in the name**.

---

### Run Every Hour

```
0 * * * * touch file301.txt
```

Runs at the **start of every hour**.

---

### Run Daily at 2 AM

```
0 2 * * * touch file301.txt
```

Runs **daily at 2:00 AM**.

---

# Practice Requirements

### Requirement 1
Create a file in `/media` directory with name **jarvis301.txt** at **9:45 PM on 11th September**.

### Requirement 2
Display message on terminal:

```
Welcome guys in cdec_b20 batch
```

at **8:10 PM every Monday**.

### Requirement 3
Display message:

```
Hello students
```

after every hour on **10th of Jan, Feb, March, Aug, Sept, Nov**.

---

# Practice Questions

1. Schedule a job to run at the **10th minute of every hour**.  
2. Run a cron job **daily at 6:00 AM**.  
3. Run a cron job **every Sunday at midnight**.  
4. Run a cron job on the **1st day of every month**.  
5. Run a cron job **every weekday (Monday–Friday) at 9 AM**.  
6. Run a cron job **at 10:30 PM on 15th August**.  
7. Run a cron job **every 2 hours**.  
8. Run a cron job **every day at 12:15 PM**.  
9. Run a cron job **at 5:45 AM every Saturday**.  
10. Run a cron job **on the 10th day of every month at 8:00 PM**.  
11. Run a cron job **every 30 minutes**.  
12. Run a cron job **at 11:59 PM on 31st December**.

---
