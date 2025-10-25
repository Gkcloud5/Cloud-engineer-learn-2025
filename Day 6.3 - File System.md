
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
	* Table based system --> Keeps a map where each files are stored on disk
	* Linked allocation --> Each file block points to the next block
* A long index point's where each file's entries point to its next part

#### 6.3.4.2  Inodes:
* Each file has its own ID card containing all its details
* Metadata includes
	* File size
	* Owner
	* Permission
	* Timestamp
* Inodes does not store name alone
* Inode points to data blocks directly
* Used in linux system

### 6.3.5 File Permission:
* Decides who read, write, execute a file
* Each file has
	* Owner
	* Group
	* others
* OS checks permission before allowing access,