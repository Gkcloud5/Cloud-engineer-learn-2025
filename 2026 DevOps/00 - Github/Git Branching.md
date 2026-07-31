
### Pain point:
* When we add new feature on existing app we can't work on live production code right? but we have to add a feature in that place branch will come and simplify it
* Branch is kind of main source but doing things and changing it does not affect to main until we merge it
* Mostly it will be
	* Specific feature
	* bug fix
	* experiment without affecting stable code

### Core Concept:
* Every project starts with primary branch usually name main or master
* Lightweight pointer: 
	* Branch is not a copy of all files. it is just tiny pointer to specific commit
* Independent history:
	* When create a new branch, we can add new commits to it while the `main` branch remains untouched and stable.


### Essential branching commands:

```
git branch       //List all the branches in current repo
git branch <branch name>    //Create new branch with that name
git switch <branch name>   //Switches working directory to that branch
git checkout -b <branch name>  //creates a new branch and switches to it 
git merge <branch name>  //Intgrates the history and changes the specified branch in curret active branch
git branch -d <branch-name>  //Deletes the branch once you are done with it
```


### Branching workflow:

1. Create & switch: Leave `main` to work on feature: `git checkout -b login-page`
2. Work & Commit: You write the code and save it: `git commit -m "Add login form"`
3. Switch back: Return stable line: `git checkout main`
4. Merge: Bring new feature into the main project: `git merge login-page`

