
### 8.1 What is hotfix branch?
* A hotfix branch is created directly from production branch
* Why?
	* Because production must be fix immediately.
```
Flow:
main --> hotfix/urgent-bug
fix --> test --> merge into main --> tag release --> deploy
AND
merege into dev (so dev also receives the fix)
```

