
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

### 4.2.2 SJF:
* Smallest burst time runs first
* Problem: need to know burst time in advance

|Process|Burst Time|Waiting Time|Turnaround Time|
|---|---|---|---|
|P2|3|0|3|
|P1|5|3|8|
|P3|8|8|16|
avg.waiting.time = 3.67ms
avg.tat = 9ms

### 4.2.3 Round Robin:
* Each process get a small fixed time --> time quantum
* Fair to all process -- Perfect for time sharing systems like modern OS

|Process|Burst Time|Waiting Time|Turnaround Time|
|---|---|---|---|
|P2|3|0|3|
|P1|5|3|8|
|P3|8|8|16|
**Average Waiting Time:** (6 + 4 + 9) / 3 = **6.33 ms**  
**Average Turnaround Time:** (11 + 7 + 17) / 3 = **11.67 ms**

### 4.2.4 Priority scheduling:
* 