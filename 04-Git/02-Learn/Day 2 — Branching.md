
### 2.1 What is branch?
* Branch is separate workspace
* You can
	* Add new feature
	* Test ideas
	* Fix bugs
	* Break things safely
* ..without touching the main project

Main branch = stable production code

In companies
* main --> always deployable
* dev --> team working branch
* feature/* --> Per developer feature

### 2.2 Why do companies use branches?
- Because
	- Everyone works without disturbing each other
	- Safe testing
	- Code review become easy
	- CI/CD can deploy only from selected branches
	- Rollback is very easy if something is goes wrong

### 2.3 Branching setup:

```
main (already exist)
dev --> Team development branch
feature/login --> a simple feature branch
feature/homepage --> another feature
```

### 2.4 what is Fast-Forward merge?
```
If main has no new commits and dev is ahead, git simply moves main pointer forward.
```

# **PRACTICAL TASK — Start in your repo**

### 1️⃣ Create dev branch

`git checkout -b dev`

This means:

- `-b` = create branch
    
- switch to `dev`
    

### 2️⃣ Add a new file

`echo "Dev changes" > dev.txt`

### 3️⃣ Add + commit

`git add dev.txt git commit -m "added dev file"`

### 4️⃣ Switch back to main

`git checkout main`

### 5️⃣ Merge dev → main

`git merge dev`

Since there is no conflict, you should see **Fast-forward**.

