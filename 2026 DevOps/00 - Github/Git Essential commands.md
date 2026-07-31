
### 3 Zones

```
Working Directory  →  Staging Area  →  Repository
(you edit here)       (photo setup)     (photo saved)
```

### Setup commands:

```
git --version 
git config --global user.name "GK"  //Name on every commit
git config --global user.email "email@gmail.com" //Email on every commit
```

### Daily work commands:

```
git init   //Turn a normal folder into gir repo
git status //Where am I? what changed? 
git add file.txt  //Put one file in the staging area
git add . //Stage everything changed
git commit -m "message"  //click the photo -- save the snapshot
git log  //See the whole album, newest first
git log --oneline  //same, but short and redable
git diff 
```