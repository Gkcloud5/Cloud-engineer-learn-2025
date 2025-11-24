
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
	* When stability is important and clear sepea