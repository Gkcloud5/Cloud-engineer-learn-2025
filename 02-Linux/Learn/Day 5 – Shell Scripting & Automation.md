
```
Script will help to run repititative tasks
```

### What is shell script?
* It's list of commands that saved in a file
* By using that you can make automation for repetitive tasks

### Things to remember on script writing:
1. Always start with shebang
	1. Tell linux which shell should execute the script
2. Use comments generously
	1. Help to understand the program part even if another developer will develop the product
3. Test commands before automating them
	1. Run commands in terminal first, if they work safely then  add to script
4. Use variables to avoid repetition
5. Add error handling
	1. &&, ||, set -e


|Problem|Without Scripts 😩|With Scripts 😎|
|---|---|---|
|Backups|You forget sometimes|Script does it daily|
|Server maintenance|You log in to 5 servers|One script updates all|
|Deployments|Manual commands (risk of mistakes)|Automated, predictable steps|
|Monitoring|You check logs manually|Script emails you only on errors|
|Time|Hours wasted repeating tasks|Saved and reused every time|

