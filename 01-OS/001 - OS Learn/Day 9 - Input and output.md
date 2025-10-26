
**Here we are going to see how OS handles input and output request from hardware like keyboard, Mouse, Printer, etc...**


### 9.1 What is IO management:
* Every IO operations data transfer between hardware to CPU
* Hardware devices are slow so OS act as middle manager and avoid time delay


### 9.2 Key technique in IO management:
#### 9.2.1 Buffering:
* When data is transferred between devices of different speed then OS uses buffer to smooth out speed mismatch.
* Temporary holding space

#### 9.2.2 Caching:
* Fast data reuse
* Storing recently used data for quick reuse

#### 9.2.3 Spooling:
* It means queueing IO tasks so slow devices can process them one at a time
* Ex: Printer

### 9.3 Device Drivers:
* The translator between OS and hardware
* It's specialized software that lets the OS communicate directly with hardware devices
* Functions:
	* Converts OS instruction into device specific signals


### 9.4 Interrupt Handling:
* An interrupt is signal sent by a devices to get CPU attention
* Process:
	* Device sends interrupt signal
	* CPU saves its current state --> context switch
	* OS identifies interrupt and runs the correct handler
	* After servicing CPU resumes previous work

### 9.5 Why it's important:
* It keeps CPU busy
* Prevent data loss due to missmatch speed
* Increase system efficiency
* Allows true multitasking