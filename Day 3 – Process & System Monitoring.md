
```
Understading how linux runs programs and how to control them.
```

### What is process?
* A process is a program in execution, a running instance of application

### Viewing process:
1. `ps` --> Snapshot of running process
	1. Process Status
	2. `ps aux`
2. `top` -- real time monitor process

### Managing process:
1. Kill process
	1. `kill <pid>` --> stop a process
	2. `kill -9 <pid>` --> force kill process
2. `nice` -- Set process priority
	1. `nice -n 10  fileName`
		1. Lower values --> Higher priority
		2. Higher values --> 