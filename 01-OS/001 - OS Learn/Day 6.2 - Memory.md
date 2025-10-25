
**Here we are going to see how OS use limited RAM to complete the process efficiently**

### 6.2.1 What is memory management?
* Every process in OS needs memory to run or execute program
* Memory manager decides:
	* Who gets memory and how much
	* When to swap in and out
	* How to protect one memory to another
	* How to run smoothly without crashing or overlapping

```
Memory management will do allocate, organise and optimize system memory(RAM + Virtual memory)
```

### 6.2.2 Memory layout of a process:
* Every process in memory divided into logical section
	* Stack
	* Heap
	* Data segment
	* Code segment

	  ``
	  |----------------------------|  High Memory
|         Stack              |  🔻 Grows Downward
|----------------------------|
|         Heap               |  🔺 Grows Upward
|----------------------------|
|         Data Segment       |  (global/static variables)
|----------------------------|
|         Code Segment       |  (program instructions)
|----------------------------|  Low Memory

```
