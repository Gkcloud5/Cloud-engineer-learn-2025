
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