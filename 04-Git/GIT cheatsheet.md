
# 🧾 Mini Git Cheatsheet — the 30% of commands that solve 90% of problems

Use these every day:

Basics

```
git status
git add <file>
git commit -m "type(scope): message"
git push               # push current branch (if tracking)
git push -u origin BR  # first push and set upstream
git pull --rebase      # update current branch cleanly
```

Branches & merges

```
git checkout -b feature/xx
git checkout main
git merge feature/xx
git branch -d feature/xx
```

Conflict resolution

```
# resolve markers in files, then:
git add <file>
git rebase --continue   # or git merge --continue (or commit)
git rebase --abort      # to cancel rebase
```

History & fixes

```
git log --oneline --graph
git reflog
git revert <bad-commit>
git reset --hard <commit>      # DANGEROUS on shared branches
git push --force-with-lease    # safe-ish force update
```

Advanced day-to-day

```
git stash
git stash pop
git cherry-pick <commit>
git rebase -i HEAD~N
git bisect start; git bisect bad; git bisect good <sha>
git tag -a vX.Y.Z -m "message"; git push origin vX.Y.Z
```
