
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
	* Accounting info -- Importance of process, CPU time
----
### Context switching:
* CPU switches from one process to another, it performs context switching
* Steps:
	* Save current state into PCB
	* Load the next process state from it's PCB
	* Resume execution
* Too many context switching slow down performance

---
### How OS manages process efficiently:
* **Schedulers** decide which process runs next
* **Priorities** ensure urgent tasks get more CPU time
* **Synchronization** prevents conflicts when multiple processes share resources
