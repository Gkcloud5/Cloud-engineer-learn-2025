
# Title: Real world Devops small simulation
## 10.1 Real company environment
1. Multiple Developers
2. PRs
3. conflicts
4. CI
5. releases
6. rollback
7. emergency hotfix
8. merge policies
9. tagging


## 10.2 Full devops flow:
* Let consider 3 developers working simultaneously
	* Dev A -- works on login feature
	* Dev B --> works on dashboard
	* Me(Devops) --> review, merge, fix, conflicts, tag, release

### 10.2.1  Step 1: Prepare repo:
```
1. go to working directory
2. checkout branch
3. pull first to make sure all changes are in local
```

```
cd ~/git-day1
git checkout main
git pull
```



### 10.2.2 Step2: Create Developer A branch:
* feature/login
```
1. create new branch
2. working on it
3. commit and push
```

### 10.2.3 Developer B branch:
* Dashboard related work
```
1. Create branch for dashboard
2. working code
3. commit and push to branch
```

==> Once all okay create PR on github

### 10.2.4 Create conflict
* Edit same file in different branch
```
1. Dev A
   echo "Conflict A line" >> conflict.txt
```

```
1. Dev B
	echo "Conflict A line" >> conflict.txt
```

### 10.2.5 resolve conflict:
```
1. Checkout dashboard branch
2. pull and fetch 
3. merge with main
4. edit conflict file
5. add and commit and push
```

### 10.2.6 Relesae tag:
```
1. checkout main
2. pull 
3. git tag with commit version
4. git push tag
5. CI will trigger and take code to deployement
```

### 10.2.7 Production problem: Rollback
```
1. Issue with new tag code
2. Rollback previous version
```

### 10.2.8 Hotfix:
```
1. Let consider need to implememt hotfix in production code
2. Create specific branch for it and work
3. add and commit changes
4. checkout main and merge with new branch
5. push the content and use new tag version to know better
6. push the tag
7. Finally need to update the changes to dev   
```
