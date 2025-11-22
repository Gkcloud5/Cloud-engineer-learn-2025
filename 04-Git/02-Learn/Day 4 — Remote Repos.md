
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
