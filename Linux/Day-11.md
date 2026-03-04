# Managing Permissions in Linux

## Importance of File Permissions in Linux

File permissions play a vital role in Linux security and system stability. They determine who can read, write, or execute files and directories, protecting sensitive data and preventing accidental or malicious changes.

### Key Reasons for File Permissions
- **System Security**: Prevent unauthorized access
- **Data Integrity**: Ensure only authorized users can modify data
- **Operational Stability**: Restrict critical system files from unauthorized modifications

---

## Explanation of rwx (Read, Write, Execute) Permissions

Linux permissions are represented using three sets of characters:

- **Read (r)**: Allows viewing file contents or listing directory contents
- **Write (w)**: Allows modifying file contents or creating/deleting files
- **Execute (x)**: Allows running a file or accessing a directory

### Permission Categories
Permissions are grouped into three categories:
- **User (u)**: Owner of the file
- **Group (g)**: Group assigned to the file
- **Others (o)**: All other users

### Example
```
-rwxr-xr-- 1 user group 1024 Dec 18 10:00 example.txt
```

Explanation:
- `rwx` → Owner permissions (read, write, execute)
- `r-x` → Group permissions (read, execute)
- `r--` → Others permissions (read only)

---

## Permissions Applied to Files and Directories

### Permission Table

| Permission | Applied to Files | Applied to Directories | Letter | Number |
|----------|-----------------|------------------------|--------|--------|
| Read     | Open a file     | List directory contents| r      | 4      |
| Write    | Modify a file   | Create/delete files    | w      | 2      |
| Execute  | Run a file      | Access directory (cd)  | x      | 1      |

---

## Changing Permissions Using Letters (Symbolic Mode)

### Syntax
```bash
chmod <u,g,o><+,-,=> <r,w,x> <file_or_dir>
```

### Note
- `=` assigns only specified permissions
- Existing permissions are removed when `=` is used

### Symbols Reference

- **u** → Owner  
- **g** → Group  
- **o** → Others  

- **+** → Add permission  
- **-** → Remove permission  
- **=** → Assign permission  

- **r** → Read  
- **w** → Write  
- **x** → Execute  

---

## Managing Permissions on Directories

| Permission | Result |
|----------|--------|
| r--      | List directory (`ls`) |
| --x      | Access directory (`cd`) |
| -w-      | Create/delete files |

---

## Managing Permissions on Files

| Permission | Result |
|----------|--------|
| r--      | Read file (`cat`, `less`, `more`) |
| --x      | Execute script/application |
| -w-      | Edit file |

---

## Practical Permission Examples

Create directory:
```bash
mkdir CDEC_B16
```

Default permissions:
```
rwx r-x r-x
```

Give write permission to group:
```bash
chmod g+w CDEC_B16
```

Remove read & execute permission from others:
```bash
chmod o-rx CDEC_B16
```

Assign read-only permission to group and others:
```bash
chmod g=o=r CDEC_B16
```

Give full permission to group and read-only to others:
```bash
chmod g+rwx,o+r CDEC_B16
```

Remove execute from group and write & execute from others:
```bash
chmod g-x,o-wx CDEC_B16
```

---

## Changing Permissions Using Octal (Numeric) Mode

### Syntax
```bash
chmod <octal_number> <file_or_dir>
```

### Permission Values
- `r = 4`
- `w = 2`
- `x = 1`

### Octal Representation

| Number | Permission |
|------|------------|
| 0 | --- |
| 1 | --x |
| 2 | -w- |
| 3 | -wx |
| 4 | r-- |
| 5 | r-x |
| 6 | rw- |
| 7 | rwx |

Example:
```
762 → rwx rw- -w-
```

---

## Practice Questions (Files)

1. File202.txt → u=rw, g=r, o=---   [ ]  
2. File203.txt → u=r, g=rwx, o=---  [ ]  
3. File204.txt → u=w, g=---, o=x    [ ]  
4. File205.txt → u=r, g=---, o=x    [ ]  
5. File206.txt → u=r, g=wx, o=r     [ ]  
6. File207.txt → u=rwx, g=rwx, o=r  [ ]  

---

## Practice Questions (Directories)

1. Dir301 → u=rwx, g=r, o=---  [ ]  
2. Dir302 → u=r, g=r, o=---    [ ]  
3. Dir303 → u=rwx, g=---, o=---[ ]  
4. Dir304 → u=---, g=rwx, o=---[ ]  

---

## Full Permissions

- Directory → `777`
- File → `666`

---

## Introduction to File Types in Linux

Linux files are categorized based on their purpose and usage.

### File Types Shown by `ls -l`

#### User Defined Files
- **Regular File (-)** → Normal file
- **Directory (d)** → Folder
- **Symbolic Link (l)** → Shortcut to another file

#### System Defined Files
- **Socket (s)** → Inter-process communication
- **Pipe (p)** → Data flow between processes
- **Block Device (b)** → Storage devices (HDD)
- **Character Device (c)** → Input devices (keyboard)
