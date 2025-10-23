
### 4.1 What is CPU scheduling:
* When multiple programs are waiting for CPU, the OS must choose which one to run next, this is done by CPU scheduler.
* **Why it's matter:*
	* Improves *CPU utilization*
	* Reduces *waiting time*
	* Increase *throughput*
	* Keeps system responsive

### 4.2 Types of CPU scheduling:
* **Non-Preemptive**
	* Once process is starts, it runs until completion
		* FCFS, SJF
* **Preemptive:**
	* OS can interrupt and switch to another process
		* Round robin, Priority

### 4.2.1 FCFS:
* The first process arrive will get CPU first

|Process|Burst Time|Waiting Time|Turnaround Time|
|---|---|---|---|
|P1|5|0|5|
|P2|3|5|8|
|P3|8|8|16|

avg.wait.time = 4.33ms
avt.tat = 9.67ms
* Simple but can cause **convoy effect**
	* Long process delay short ones
* 