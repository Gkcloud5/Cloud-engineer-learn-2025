### Overview:
* Git is version control system. it tracks every change make in code files over time
	* Any time we can go back to any previous version
	* See who changed and what and when
	* Work on same code with team , without overwriting other work
* Every developer worked on their own copy branch and merged carefully
* Concepts
	* Repo -- A folder that git is tracking. project home
	* Commit -- A saved snapshot of code at point in time
	* Branch -- A separate workspace to try new idea without touching the main code
	* Merge -- Combining changes from one branch to another
	* Clone -- Downloading copy of someone else repo to our machine
	* Push -- Uploading local changes to remote
	* Pull -- Downloading latest changes from remote to local

### How git works:

```
Your Code  →  git add  →  git commit  →  git push  →  GitHub/Remote Repo
(edited)      (stage it)   (save snap)   (upload it)
```

### Branch Strategy:

```
main(production -- live website)
└── develop (stable development) 
	├── feature/user-login
	├── feature/payment-gateway 
	└── hotfix/critical-bug-fix
```

### How it used in AWS specifically:

1. write cloudformation templates
2. Lambda function code -- track every version
3. CI/CD with codepipeline -- Push to 