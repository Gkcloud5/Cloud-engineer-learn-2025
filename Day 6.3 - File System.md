
```
How OS is stores, organizes and protects data using file system, directory structure and permission
```

### 6.3.1 What is File system?
* A file system is the OS's method of organizing and tracking files on storage devices like SSD, HDD
* without file system OS does not know where is file begin and end
* It handles
	* Where files are stored in disk
	* How they names and organized
	* Who can access and modify

### 6.3.2 Main Components of file system:
1. Directory structure --> Organizes files in a hierarchical way 
2. File Allocation Table --> Keeps track of which disk blocks stores which part of a file
3. Inodes --> Contain file meta data
	1. Size, permission, owner, timestamp like information
4. File Permission --> Control who can read and write
5. Security --> Secure unauthorized users can't access sensitive data

### 6.3.3 Directory Structure:
* Most OS uses hierarchy directory structure
* Common directory structure
	* Single-level --> All files in one directory
	* Two-level --> Separate directory for each user
	* Tree-structure --> Hierarchical system with sub directory
	* Acryclic graph --> Allow shared file via links
		* Hard links

### 6.3.4 How files are tracked?
* By using FAT or Inodes
#### 6.3.4.1  FAT:
* File allocation table
	* Using in windows
	* 