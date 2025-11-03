
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
		2. Higher values --> lower priority

### System info commands:

| Command         | Purpose                            | Example Output                     |
| --------------- | ---------------------------------- | ---------------------------------- |
| `df -h`         | Disk Free space                    | See available storage on drives    |
| `du -shfolder/` | Disk Usage                         | Check how much space a folder uses |
| `free -h`       | Memory usage                       | See total, used, free RAM          |
| `uptime`        | How long the system’s been running | “up 3 days, 2 hours”               |
| `uname -a`      | System info                        | Kernel version, OS type            |
| `dmesg`         | Kernel messages                    | Hardware and boot logs             |
