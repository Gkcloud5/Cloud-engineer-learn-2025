
### File permissions:
1. cp --> Copy files
2. mv
3. rm --> remove files
4. mkdir --> make directory
5. touch --> create a empty file

### wildcards:
1. it will used to select or doing operation with multiple files at same time
	1. *  --> Any number of characters
	2. ? --> One single character

### File Permission:
* Every file have 3 type of permission and 3 type of users
	* 3 user categories
		* u --> user
		* g --> group
		* o --> others
	* 3 Permission
		* r --> read
		* w --> write
		* x --> execute

### Permission commands
* chmod --> change file permission
* chown --> change owner
* chgrp --> change group

|Number|Meaning|Permission|
|---|---|---|
|7|4+2+1 = rwx|Full|
|6|4+2 = rw-|Read + Write|
|5|4+1 = r-x|Read + Execute|
|4|4 = r--|Read only|