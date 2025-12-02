
## 11.1 Overview:
* Today we will know more about senior level GIT.
* Some commands usage will separate DevOps engineer from regular developer, here we are going to see that type of commands

### 11.2 Advanced GIT:
* Commands:
	* stash
	* cherry-pick
	* rebase -i
	* reflog
	* bisect
	* clean
	* safe force-push
	* commit squashing
	* history recovery
* These commands are used on following scenario:
	* Something goes wrong
	* A developer breaks a branch
	* CI is failing
	* A commit must be moved
	* Production must be recovered
	* A PR needs cleanup


### 11.2.1 `git stash` - save work without committing:
* When to use:
	* You are working on something but need to switch branches OR pull latest code, but work is incomplete
* Commands
	* `git stash` --> Changes disappear from working directory but are saved
	* `git stash list` --> Show stash list
	* `git stash apply` --> Apply stash back
	* `git stash top` --> Apply and remove

### 11.2.2 `git cherry-pick` - Take one commit and apply anywhere:
* When to use:
	* when FIx a bug in PR branch, but the same bug needs fixing in main - without merging the whole PR.
* Commands:
	* Commit ID: `git log --oneline`
	* `git checkout main` & `git cherry-pick <commit id>`

### 11.2.3 `git rebase -i` - Rewrite history like a senior engineer:
* Interactive rebase lets you:
	* squash commits
	* rename commits
	* delete commits
	* re-order commits
* Example:
	* `git rebase -i HEAD~5`
		* you will see
			* pick 12345 first commit
			* pick abcdef second commit
			* pick ....
		* change `pick` to `squash`
			* pick 123456 first commit
			* squash abcde second commit
	* Teams use this to keep history clean before merging PR's.

### 11.2.4 `git reflog` - Your git time-machine:
* It shows **everything git did**, even things that `git log` does NOT show.
* command
	* `git reflog`
* If reset wrongly or lose commits, recover
	* `git checkout <old-reflog-commit>`
	* Or restore branch
		* `git branch restore main <commit-id>`
* **Reflog = Disaster recovery**


### 10.2.5 `git bisect` - Find bad commit FAST:
* if bug appears but don't know which commit caused it:
	* commands:
		* `git bisect start`
		* `git bisect bad`
		* `git bisect good <old-good-commit>`
	* Mark good/bad:
		* `git bisect good`
		* `git bisect bad`
		* Git finds the exact commit that introduced the bug.


### 10.2.6 `git clean` - Remove junk files safely:
* see what would be deleted:
	* `git clean -n`
* Actually delete untracked junk:
	* `git clean -fd`
	* NEVER use if not sure

### 10