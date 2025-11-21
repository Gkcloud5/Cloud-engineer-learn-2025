
### How conflict looks like
```
<<<<<<< HEAD
Main branch edit
=======
Dev branch edit
>>>>>>> dev
```

### My jobs here, how to handle it:
* Must decide
	* Keep main version?
	* Keep dev version?
	* Keep both?
	* Modify?
* No straight answer, depends on project

* In real companies, we choose based on
	* Newest code
	* Correctness
	* Stability
	* release schedule
	* break/bug risk

### 3.3 Fix conflict -- manually:
* Need to remove the following content in conflict file 
```
<<<<<<< HEAD
=======
>>>>>>> dev

```

then need to do staging and commit

```
git add dev.txt
git commit -m "merged dev contenttt"
```

### 3.4 Verify the merge:
```
git log --online --graph
```

```
root@ubuntu:~/git-day1# git log --oneline --graph
*   c9edc05 (HEAD -> main) merged dev into main after conflict fix
|\
| * 36c53d6 (dev) Update from dev
| * e19eff7 (origin/feature/login, origin/dev, feature/login) added login feature
* | 2312edf update from main
|/
* 259c38b added dev files
* e8b13d2 (origin/main) from my linux first test
root@ubuntu:~/git-day1# git push
```
### 3.5 Push to github:

```
git push
```

