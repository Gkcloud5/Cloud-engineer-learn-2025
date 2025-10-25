
**Generally different process need to communicate within to complete their tasks on that time InterProcess Communication will help to complete it in better way and avoid conflicts**

### 6.1 What is IPC:
* Generally process are running their isolated place seems one process to another process no connection, sometime they need to connect to complete the tasks during that time IPC comes in.
	* Both process communicate between them and do works efficiently
* *IPC is a mechanism that allows process to exchange data and messages safely and efficiently*

---

### 6.2 Main IPC models:
##### 1. Message Passing
* Process communicate between by sending message by using channels managed by OS
* **Methods:**
	* Pipes --> 1 way communication
	* Message queue --> Message stored and managed in a queue
	* Sockets --> Communication across networks

##### 2. Shared Memory:
* Process share a common memory region, accessing it directly
* Feature:
	* Speed
	* Synchronization
	* Usage

---
### 6.3 Synchronization:
* When multiple process or threads shared data, they must stay synchronized to avoid inconsistency
* Common tools:
	* **Mutex** --> Only one process can access a resources at a a time
	* **Semaphores** --> Allow limited access
	* **Events/Conditions** --> Used to signal between processes --> wait/ notify pattern

---
### 6.4 Race Conditions:
* A race conditions occurs when 2 process try to modify shared data simultaneously
* Solutions:
	* Locks 
	* Semaphores

---

### 6.5 How OS manages IPC internally
* OS maintains buffer, queue, memory maps to manage communication
* It provides system calls
	* pipe()
	* shmget()
	* msgsnd()
* It ensures `process isolation + controlled data sharing`
---
### 6.6  What Happens When It’s Working (Behind the Scenes)
1. OS sets up a **communication path** (pipe, socket, shared memory).
2. Data moves either through:
    - **Kernel** (message passing) 
    - **Shared space in memory** (shared memory) 
3. Synchronization tools (locks/semaphores) ensure one process doesn’t overwrite another’s data.
4. Once communication ends, OS cleans up the channel.