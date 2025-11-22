
```
We will learn about how teams actualy move code between local and remote repositories. this is where careless user causes outages.
```

### 3 main things when in remote:
1. push
2. pull
3. fetch

#### 4.1.1 push:
* Send locally changed file to cloud -- github
* local commit to git repo

#### 4.1.2 pull:
* get all committed things from cloud - github
* Downloading the changes from remote storage

#### 4.1.3 fetch:
* download remote commits but it does not change working files or branch points
* fetch will help to know who commited and what is the change before merge


### 4.2 Simple, plain meanings of commands:
* `git push` ---> Send local commit to remote
* `git fetch` --> Download remote commits only, it does not change working files or branch pointer, good for inspection.
* `git pull` --> `git fetch` then merge - it updates current branch automatically
* `git remote` --> shows remote repo 
* `git branch -u` / `git push -u` -->  link, tells git "from now on, when i type git push, send this specific local branch to that specific remote branch"
* `git push --force-with-lease` --> force push but safer, it fails if someone else pushed meanwhile.

### 4.3 why fetch exists:

* `git pull` --> it's actually aggressive. it grabs the changes and smooshes them into your work immediately.
* `git fetch` --> it's for safety.  it let us see what is coming before you decide to merge it
	* run `git fetch`
	* run `git log`
	* Then decide, okay to merge or not

### 4.4 Commands must memorize:
#### 4.4.1 Example 1:
1. Add file in git repo
2. `git fetch`
3. `git status`
	1. _(It should tell you: "Your branch is behind 'origin/main' by 1 commit.")_
4. `git pull`

#### 4.4.2 Example 2:
1. Add file in git repo
2. create a file in local repo but in different name and commit it
3. `git fetch`
4. `git status`
	1. "Your branch and 'origin/main' have **diverged**," "and have 1 and 1 different commits each."
5. `git pull --no-rebase`
6. `git log --oneline --graph -n 5`


```
root@ubuntu:~/git-day1# ls
a.txt  b.txt  c.txt  dev.txt  login.txt
root@ubuntu:~/git-day1# git fetch
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (3/3), 949 bytes | 316.00 KiB/s, done.
From https://github.com/Gkcloud5/GitLearn
   c9edc05..eb5c615  main       -> origin/main
root@ubuntu:~/git-day1# git fetch
root@ubuntu:~/git-day1# ls
a.txt  b.txt  c.txt  dev.txt  login.txt
root@ubuntu:~/git-day1# git status
On branch main
Your branch is behind 'origin/main' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)

nothing to commit, working tree clean
root@ubuntu:~/git-day1# git pull
Updating c9edc05..eb5c615
Fast-forward
 cloud.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 cloud.txt
root@ubuntu:~/git-day1# ls
a.txt  b.txt  cloud.txt  c.txt  dev.txt  login.txt
root@ubuntu:~/git-day1#
root@ubuntu:~/git-day1#
root@ubuntu:~/git-day1# echo "I am working locally" > local.txt
root@ubuntu:~/git-day1# git add local.txt
root@ubuntu:~/git-day1# git commit -m "Added local work"
[main dae094d] Added local work
 1 file changed, 1 insertion(+)
 create mode 100644 local.txt
root@ubuntu:~/git-day1# git fetch
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (3/3), 942 bytes | 942.00 KiB/s, done.
From https://github.com/Gkcloud5/GitLearn
   eb5c615..e3a5062  main       -> origin/main
root@ubuntu:~/git-day1# git status
On branch main
Your branch and 'origin/main' have diverged,
and have 1 and 1 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

nothing to commit, working tree clean
root@ubuntu:~/git-day1# git pull
hint: You have divergent branches and need to specify how to reconcile them.
hint: You can do so by running one of the following commands sometime before
hint: your next pull:
hint:
hint:   git config pull.rebase false  # merge
hint:   git config pull.rebase true   # rebase
hint:   git config pull.ff only       # fast-forward only
hint:
hint: You can replace "git config" with "git config --global" to set a default
hint: preference for all repositories. You can also pass --rebase, --no-rebase,
hint: or --ff-only on the command line to override the configured default per
hint: invocation.
fatal: Need to specify how to reconcile divergent branches.
root@ubuntu:~/git-day1# ls
a.txt  b.txt  cloud.txt  c.txt  dev.txt  local.txt  login.txt
root@ubuntu:~/git-day1#
root@ubuntu:~/git-day1# git pull --no-rebase
Merge made by the 'ort' strategy.
 team.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 team.txt
root@ubuntu:~/git-day1# git log --oneline --graph -n 5
*   5c6e163 (HEAD -> main) Merge branch 'main' of https://github.com/Gkcloud5/GitLearn
|\
| * e3a5062 (origin/main) Create team.txt
* | dae094d Added local work
|/
* eb5c615 Create cloud.txt
*   c9edc05 merged dev into main after conflict fix
|\
root@ubuntu:~/git-day1# ls
a.txt  b.txt  cloud.txt  c.txt  dev.txt  local.txt  login.txt  team.txt
root@ubuntu:~/git-day1#

```


