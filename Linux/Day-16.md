# Introduction to Search and Filter Utilities

Search and filter utilities are essential tools in Linux for processing and analyzing text data.  
They allow DevOps engineers to efficiently **locate, manipulate, and extract information** from files and command outputs.

---

# 🔹 What Are Search and Filter Utilities?

- **Search** → Find specific patterns or content within files  
- **Filter** → Extract, sort, or modify data streams  

---

# 🔹 Common Use Cases

- Analyzing **log files for errors**
- Extracting **specific data from reports**
- Finding **configuration issues**

---

# Overview of Key Utilities

## 🔹 grep

**Purpose:** Search for patterns in files or input streams

**Key Features**
- Regular expressions
- Case-insensitive search
- Line numbers

**Use Case**
- Find specific text in logs or code files

Example:

```bash
grep "error" logfile.txt
```

---

## 🔹 cat

**Purpose:** Concatenate and display file contents

**Key Features**
- Display files
- Combine multiple files
- Show line numbers

**Use Case**
- View file contents
- Create new files from input

Example:

```bash
cat file.txt
```

---

## 🔹 sort

**Purpose:** Sort lines of text files or input streams

**Key Features**
- Alphabetical sorting
- Numerical sorting
- Reverse order
- Unique sorting

**Use Case**
- Organize data
- Remove duplicates
- Prepare reports

Example:

```bash
sort file.txt
```

---

## 🔹 uniq

**Purpose:** Remove duplicate lines from sorted input

**Key Features**
- Show only unique lines
- Count occurrences
- Compare adjacent lines

**Use Case**
- Clean data
- Identify duplicates
- Generate summaries

Example:

```bash
uniq file.txt
```

---

# Read Files Using cat, sort, and uniq

These utilities work together to **read, process, and organize file contents**.

---

# 🔹 Using cat to Read Files

### Basic File Reading

```bash
cat file.txt
```

Output: Displays entire file content

---

### Read Multiple Files

```bash
cat file1.txt file2.txt
```

---

### Show Line Numbers

```bash
cat -n file.txt
```

Example Output:

```
1  First line
2  Second line
3  Third line
```

---

# 🔹 Using sort to Organize Content

### Basic Alphabetical Sort

```bash
sort file.txt
```

Output: Lines sorted **A → Z**

---

### Numerical Sort

```bash
sort -n numbers.txt
```

Input:

```
10
2
1
```

Output:

```
1
2
10
```

---

### Reverse Sort

```bash
sort -r file.txt
```

Output: **Z → A order**

---

# 🔹 Using uniq to Remove Duplicates

`uniq` requires **sorted input** to work properly.

### Remove Duplicate Lines

```bash
sort file.txt | uniq
```

Input:

```
apple
banana
apple
cherry
```

Output:

```
apple
banana
cherry
```

---

### Count Occurrences

```bash
sort file.txt | uniq -c
```

Output:

```
2 apple
1 banana
1 cherry
```

---

### Show Only Duplicates

```bash
sort file.txt | uniq -d
```

Output:

```
apple
```

---

### Show Only Unique Lines

```bash
sort file.txt | uniq -u
```

Output:

```
banana
cherry
```

---

# Introduction to the find Utility

`find` is a powerful command-line utility used to **search files and directories based on various criteria**.

---

# 🔹 find vs Other Search Tools

| Tool | Purpose |
|-----|--------|
| locate | Fast database search (requires `updatedb`) |
| which | Find executable files in PATH |
| whereis | Find binaries, sources, manuals |
| find | Comprehensive search with full control |

---

# Basic Syntax of find

```bash
find [path] [expression]
```

- **path** → Starting directory (default: current directory)
- **expression** → Search criteria and actions

---

# 🔹 Basic Examples

### Find All Files in Current Directory

```bash
find .
```

Lists all files and subdirectories recursively.

---

### Find Files in Specific Directory

```bash
find /home/labex/project
```

---

### Find File by Name

```bash
find . -name "file.txt"
```

---

### Case-Insensitive Search

```bash
find . -iname "FILE.txt"
```

---

# Advanced Usage and Filtering Options

## 🔹 Filter by Type

```bash
find . -type f     # Files only
find . -type d     # Directories only
find . -type l     # Symbolic links
```

---

## 🔹 Filter by Name Pattern

```bash
find . -name "*.txt"
find . -iname "*.TXT"
```

---

## 🔹 Filter by Size

```bash
find . -size +100M
find . -size -1k
find . -size 10M
find . -size +1G
find . -size -2G
find . -size 1G
```

Meaning of symbols:

| Symbol | Meaning |
|------|---------|
| + | Greater than |
| - | Less than |
| none | Exact size |

---

## 🔹 Filter by Time

```bash
find . -mtime -7
find . -mtime +30
find . -mtime 7
```

Meaning:

- `-7` → Modified in last 7 days  
- `+30` → Modified more than 30 days ago  
- `7` → Modified exactly 7 days ago  

---

## 🔹 Combining Filters

```bash
find . -name "*.log" -mtime -7
```

Find `.log` files modified in the **last 7 days**.

---

# Practical Examples

## 🔹 Find by Name

```bash
find /home -name "*.txt"
```

---

## 🔹 Find by Type

```bash
find . -type f
find . -type d
find . -type l
```

---

## 🔹 Find by Size

```bash
find . -type f -size +1G
find . -type f -size -100k
find . -type f -size 1M
```

---

## 🔹 Find by Modification Date

```bash
find . -type f -mtime -1
find . -type f -mtime +30
```

---

### Files Accessed in Last Hour

```bash
find . -type f -amin -60
```

---

### Find Files Owned by User

```bash
find . -user pratham
```

---

### Find Empty Files and Directories

```bash
find . -empty
```

---

# Shortcuts

| Command | Purpose |
|-------|---------|
| grep | Searches patterns in text |
| cat | Displays and concatenates files |
| sort | Organizes lines alphabetically or numerically |
| uniq | Removes duplicates from sorted input |
| find | Locates files by name, type, size, date |

💡 Combine utilities with **pipes (`|`)** for powerful data processing.

---

# 📝 Quick Reference: Search and Filter Commands

## GREP – Search Patterns

```bash
grep "pattern" file.txt
grep -i "pattern" file.txt
grep -n "pattern" file.txt
grep -v "pattern" file.txt
```

---

## CAT – Display Files

```bash
cat file.txt
cat -n file.txt
```

---

## SORT – Sort Lines

```bash
sort file.txt
sort -n numbers.txt
sort -r file.txt
sort -u file.txt
```

---

## UNIQ – Remove Duplicates

```bash
uniq file.txt
uniq -c file.txt
uniq -d file.txt
uniq -u file.txt
```

---

## FIND – Locate Files

```bash
find . -name "*.txt"
find . -type f
find . -type d
find . -size +1M
find . -mtime -7
```
