# 🐧 Day 5: Delving Deep into the Linux File System

![Linux](https://img.shields.io/badge/Linux-File%20System-yellow?logo=linux)
![CLI](https://img.shields.io/badge/CLI-Commands-black?logo=gnubash)
![Level](https://img.shields.io/badge/Level-Beginner-blue)
![Practice](https://img.shields.io/badge/Hands--On-Practice-green)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

# 📂 Navigating the File System

Understanding how to navigate the Linux file system is fundamental to using the operating system effectively.

The Linux file system is organized as a hierarchy, starting from the root directory:

```
/
```

---

## 🔑 Key Commands for Navigation

### 📍 pwd
Prints the current working directory.

### 📁 cd
Changes the current directory.

```bash
cd /home/user
cd ..
cd -
```

### 📄 ls
Lists the contents of a directory.

```bash
ls -l
ls -a
```

---

# 📁 File and Directory Management

## 🆕 Creating Files and Directories

```bash
touch filename
mkdir dirname
```

---

## ✏️ Editing Files

### nano

```bash
nano filename
```

Save → Ctrl + O  
Exit → Ctrl + X  

### vim

```bash
vim filename
```

Press `i` → Insert mode  
Press `Esc` → Exit insert mode  
Type `:wq` → Save and quit  

---

# 📌 Commands for Working with Files & Directories

| Command | Description |
|----------|------------|
| pwd | Present working directory |
| cd | Change directory |
| ls | List files |
| ll | Detailed file listing |
| cat | View file content |
| cp | Copy file |
| mv | Move / Rename |
| mkdir | Create directory |
| rmdir | Delete empty directory |
| rm | Delete file/directory |
| locate | Search |
| find | Advanced search |
| sudo | Admin privileges |
| head | First 10 lines |
| tail | Last 10 lines |
| echo | Save data into file |

---

# ⌨️ Linux Shortcuts

Tab → Auto-complete  
Ctrl + C → Cancel process  
Ctrl + Z → Suspend process  
Ctrl + D → Logout  
Ctrl + L → Clear terminal  
Ctrl + A → Move to beginning  
Ctrl + E → Move to end  
Ctrl + U → Delete to beginning  
Ctrl + W → Delete word  
Ctrl + Y → Paste  
Ctrl + P → Previous command  
Ctrl + R → Reverse search  

---

# 📖 READ Operations

## cat
```bash
cat <file_name>
```

## more
```bash
more <file_name>
```

## less
```bash
less <file_name>
```

## head
```bash
head <file_name>
head -n 15 <file_name>
```

## tail
```bash
tail <file_name>
tail -n 15 <file_name>
```

## sort
```bash
sort <file_name>
sort -r <file_name>
```

---

# 🚚 MOVE Operation

```bash
mv <source> <destination>
```

Move example:

```bash
mv /root/anaconda /mnt/
mv /root/* /mnt
```

Rename directory:

```bash
mv dir1 dir2
```

Rename file:

```bash
mv file1.txt file2.txt
```

---

# 📋 COPY Operation

```bash
cp <source> <destination>
```

Options:
- -f → force
- -v → verbose
- -r → recursive

Examples:

```bash
cp -r /etc /mnt/etc-bkp
cp /root/* /media
cp -rv file1.txt file2.txt /mnt
```

---

# 🗑️ Deleting Files

```bash
rm filename
rm -i filename
rm -r directory
rm -rf directory
```

---

# 🎯 Conclusion

Mastering Linux file system commands makes navigation and file management efficient.

Practice daily to build confidence and improve speed.

⭐ Keep practicing Linux commands!
