
### 2.1 What is branch?
* Branch is separate workspace
* You can
	* Add new feature
	* Test ideas
	* Fix bugs
	* Break things safely
* ..without touching the main project

Main branch = stable production code

In companies
* main --> always deployable
* dev --> team working branch
* feature/* --> Per developer feature

### 2.2 Why do companies use branches?
- Because
	- Everyone works without disturbing each other
	- Safe testing
	- Code review become easy
	- CI/CD can deploy only from selected branches
	- Rollback is very easy if something is goes wrong

### 2.3 Branching setup:

```
main (already exist)
dev --> Team development branch

```