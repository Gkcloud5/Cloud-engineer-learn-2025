
```
How OS enable single process to perform multiple tasks at the same time, efficiently and safely
```


### 5.1  What are threads?
* A thread is the smallest unit of execution inside a process
* Every process has it own thread main one

|Concept|Description|Real-Life Analogy|
|---|---|---|
|**Process**|Independent program with its own memory|A company building|
|**Thread**|Lightweight sub-task within the process|Employees in the same office|
|**CPU Core**|Executes threads|Workers doing the tasks|

---
### 5.2  Process vs Thread:

|Feature|Process|Thread|
|---|---|---|
|**Definition**|Independent program in execution|Subtask within a process|
|**Memory**|Has its own memory|Shares memory with other threads|
|**Communication**|Needs Inter-Process Communication (IPC)|Easy — shares same data|
|**Creation Time**|Slower|Faster|
|**Example**|MS Word, Chrome|Spell-check, rendering, background save|

---
### 5.3  Concurrency vs Parallelism:
* Concurrency --> Managing multiple tasks at once --> Interleaved
	* It improves `responsivesness`
* Parallelism --> Executing multiple tasks literally at the same time
	* It improves `throughput`

---

### 5.4  Benefits of multithreading:
* Responsiveness