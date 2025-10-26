
```
Here we will understand how OS avoid system freezes and protect data in system
```

### 9.2.1 What is Deadlock?
* It happens when two or more process are waiting for each other forever and none of them can continue

#### 9.2.1.1 Example scenario:
1. Process A locks File 1 and requests File 2
2. Process B locks file 2 and request file 1
	1. Both wait forever -- deadlock

#### 9.2.1.2 Necessary conditions for deadlock:
1. Mutual exclusion --> Resources can't be shared
2. Hold and wait --> process hold one resources while waiting for other
3. No preemption --> Can't be forcibly taken
4. Circular wait --> Process form cycle and wait on each other

#### 9.2.1.3 Deadlock prevention:
1. Eliminate Hold and wait --> Process requests all resources at once
2. Allow preemption --> OS can take resources away
3. Avoid circular wait --> Impose ordering on resources
4. Deny mutual exclusion --> Share resources if possible

#### 9.2.1.4 Deadlock detection and recovery:
1. Detection algorithm --> circular waiting graphs
2. Recovery: Abort or restart one process to break the cycle


### 9.2.2 What is OS security basics:
* It ensures
	* Only authorized users access resources
	* Process are isolated from each other
	* System data remains safe and private

#### 9.2.2.1 Main components of OS security:
* Authentication --> Verify users identity
* Authorization --> Grant resources access
* Encryption --> Protect stored or transmitted data
* Audit and log --> Track actions
* Virus/malware --> Monitor and isolate threats