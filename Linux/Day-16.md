Introduction to Search and Filter Utilities

Search and filter utilities are essential tools in Linux for processing and analyzing text data.  
They allow DevOps engineers to efficiently locate, manipulate, and extract information from files and command outputs.

 🔹 What Are Search and Filter Utilities?
- Search : Find specific patterns or content within files  
-  Filter : Extract, sort, or modify data streams  


 🔹 Common Use Cases
- Analyzing log files for errors  
- Extracting specific data from reports  
- Finding configuration issues  

---

 Overview of Key Utilities: grep, cat, sort, uniq

 🔹 grep
-  Purpose : Search for patterns in files or input streams  
- Key Features : Regular expressions, case-insensitive search, line numbers  
- Use Case : Find specific text in logs or code files  

 🔹 cat
- Purpose : Concatenate and display file contents  
- Key Features : Display files, combine multiple files, show line numbers  
- Use Case : View file contents, create new files from input  

 🔹 sort
- **Purpose**: Sort lines of text files or input streams  
- **Key Features**: Alphabetical/numerical sorting, reverse order, unique sorting  
- **Use Case**: Organize data, remove duplicates, prepare reports  

 🔹 uniq
- **Purpose**: Remove duplicate lines from sorted input  
- **Key Features**: Show only unique lines, count occurrences, compare adjacent lines  
- **Use Case**: Clean data, identify duplicates, generate summaries  


 Read Files Using cat, uniq, and sort

These utilities work together to read, process, and organize file contents.

 🔹 Using cat to Read Files

 Basic file reading:

cat file.txt

**Output:** Displays entire file content

 Read multiple files:

cat file1.txt file2.txt


 Show line numbers:

cat -n file.txt

**Output:**

     1  First line
     2  Second line
     3  Third line


 🔹 Using sort to Organize Content

Basic alphabetical sort:

sort file.txt

**Output:** Lines sorted A-Z

Numerical sort:

sort -n numbers.txt

**Input:**

10
2
1

**Output:**
```
1
2
10
```

Reverse sort:

sort -r file.txt
```
**Output:** Z-A order

---

🔹 Using uniq to Remove Duplicates

uniq` requires sorted input to work properly.

Remove duplicate lines:

sort file.txt | uniq

**Input:**

apple
banana
apple
cherry

**Output:**

apple
banana
cherry




Count occurrences:

sort file.txt | uniq -c


**Output:**

      2 apple
      1 banana
      1 cherry


 Show only duplicates:

sort file.txt | uniq -d

**Output:**

apple


Show only unique lines:

sort file.txt | uniq -u

**Output:**

banana
cherry


 Introduction to the find Utility


`find` is a powerful command-line utility for searching files and directories based on various criteria.







 🔹 find vs Other Search Tools

- **locate**: Fast database search (requires updatedb)  

- **which**: Find executable files in PATH  

- **whereis**: Find binaries, sources, manuals  

- **find**: Comprehensive search with full control  


---


Basic Syntax of find


🔹 Syntax Structure


find [path] [expression]


-  path : Starting directory (default: current directory)  

-  expression : Search criteria and actions  


 🔹 Basic Examples


 Find all files in current directory:

find .


**Output:** Lists all files and subdirectories recursively





Find files in specific directory:

find /home/labex/project


 Find files with specific name:

find . -name "file.txt"


 Case-insensitive name search:

find . -iname "FILE.txt"

---


Advanced Usage and Filtering Options


🔹 Filtering by Type


find . -type f    # Files only

find . -type d    # Directories only

find . -type l    # Symbolic links only



🔹 Filtering by Name Patterns


find . -name "*.txt"        # Exact match

find . -iname "*.TXT"       # Case-insensitive


🔹 Filtering by Size


find . -size +100M     # Larger than 100 MB
find . -size -1k       # Smaller than 1 KB
find . -size 10M       # Exactly 10 MB
find . -size +1G       # Larger than 1 GB
find . -size -2G       # Smaller than 2 GB
find . -size 1G        # Exactly 1 GB
Meaning of Symbols
+ → greater than


- → less than


no symbol → exact size



🔹 Filtering by Time


find . -mtime -7            # Modified in last 7 days

find . -mtime +30           # Modified more than 30 days ago

find . -mtime 7             # Modified exactly 7 days ago


 🔹 Combining Filters with Operators

find . -name "*.log" -mtime -7    

Practical Examples of Finding Files by Name, Type, Size, and Modification Date


🔹 By Name

Find all .txt files:

find /home -name "*.txt"

 🔹 By Type


Find all regular files:

find . -type f


Find all directories:

find . -type d


 Find all symbolic links:

find . -type l


---


🔹 By Size


Find files larger than 1GB:

find . -type f -size +1G


Find files smaller than 100KB:

find . -type f -size -100k


 Find files exactly 1MB:

find . -type f -size 1M







🔹 By Modification Date


 Find files modified in last 24 hours:

find . -type f -mtime -1


 Find files modified more than 30 days ago:

find . -type f -mtime +30

 Find files accessed in last hour:

find . -type f -amin -60


 Find files owned by specific user:


find . -user pratham


Find empty files and directories:

find . -empty



Shortcuts


 grep :-  searches for patterns in text  

 cat :-  displays and concatenates files  

 sort :-  organizes lines alphabetically/numerically  

 uniq :- removes duplicates from sorted input  

 find :- locates files by name, type, size, date, permissions  

 Combine utilities with pipes for powerful data processing  


---


📝 Quick Reference: Search and Filter Commands



# GREP - Search Patterns

grep "pattern" file.txt              # Basic search

grep -i "pattern" file.txt           # Case-insensitive

grep -n "pattern" file.txt           # Show line numbers

grep -v "pattern" file.txt           # Invert match


# CAT - Display Files

cat file.txt                         # Display file

cat -n file.txt                      # With line numbers



# SORT - Sort Lines

sort file.txt                        # Alphabetical sort

sort -n numbers.txt                  # Numerical sort

sort -r file.txt                     # Reverse sort

sort -u file.txt                     # Unique sort


# UNIQ - Remove Duplicates

uniq file.txt                        # Remove duplicates

uniq -c file.txt                     # Count occurrences

uniq -d file.txt                     # Show duplicates only

uniq -u file.txt                     # Show unique only


# FIND - Locate Files

find . -name "*.txt"                 # By name

find . -type f                       # Files only

find . -type d                       # Directories only

find . -size +1M                     # Larger than 1MB

find . -mtime -7                     # Modified last 7 days


