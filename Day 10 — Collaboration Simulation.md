
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



