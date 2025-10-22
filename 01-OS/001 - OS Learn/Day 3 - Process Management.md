
### What is a process:
* A process is simply a program in execution.
* OS will decide process time, priority and which process need to run those kind of things

----
### Process states:
* 5 states
	* New
	* Ready
	* Running
	* Waiting
	* Terminated
* CPU can switch process in execution place to run multiple process in short time
 ---
### Process Control Block:
* PCB stores essential details of process
* PCB field
	* Process ID
	* Program counter -- next instruction to execute
	* CPU registers -- Temporary data like storing state when context switching
	* Memory info -- Which memory segment it uses
	* IO status -- Devices assigned to it
	* Priority -- Importance of process