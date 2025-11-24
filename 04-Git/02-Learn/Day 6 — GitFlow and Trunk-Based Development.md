
### 6.1 Why do branching strategies exist?
* Because in company
	* Many developers work at the same time
	* Code needs to reach production safely
	* CI/CD pipelines depend on branch rules
	* Hotfixes must not disturb feature work
	* Release must be trackable
* `Branch strategy = rules for how your team uses GIT`

### 6.2 GitFlow:
* It will be used when company release once a week or once a month.
* They need structure.
* Branch structure:
	* `main` or `master` - This branch holds the code that is always ready to be released to the users. it is the most stable version.
	* `develop` - This main branch where all the features are put together and tested. it represents the next major release
	* Following are temporary branches
		* `feature`- Developing a new feature - created from develop. merged back into `develop` when finished
		* `release` - Preparing for new official launch - created from `develop`. used for final testing and bug fixes before the release. merged into `both` and `develop`
		* `hotfix` - Fixing critical bugs in production version, created directly from `main`. merged back into both `main` and `develop`.
* When to use it:
	* For projects that require a very strict and formal release cycle.
	* When stability is important and clear separation between development, testing and production
	* In environments where a lot of manual testing QA is required before release

### 6.3 Trunk-Based Development:
* Big companies using method
* It's simpler and most modern approach where all developers work almost on a single branch, usually called `main` or `trunk`.
* `Structure:`
	* `Main` branch: everyone commits their small changes directly to this branch or uses very short lived branches.
	* `small, frequent commits:` Key is that developer integrates their work into the main branch many times a day
	* `Feature flasgs`: to add incomplete feature or turn off feature in live code until it's ready, keeping `main` branch stable
* `Workflow`:
	* Create small feature branches
	* Work for 1 day
	* Open PR
	* CI tests
	* Merge quickly
	* Delete branch
* `When to use`:
	* For teams that practices `continuous integration and continuous delivery`. 
	* When speed and rapid feedback are the top priority.

### 6.4 Hybrid: Github Flow:
* Focusing on 2 branch `main` and ` feature`.
	* feature branch is short lived.
* Core philosophy is `continuous delivery` meaning every change is merged into main codebase and is ready to go live immediately.
* One `main` and `feature` branch, no other branch like `develop`, `hotfix`, `release`