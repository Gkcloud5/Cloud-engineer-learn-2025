
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
* When multiple process or threads shared data,