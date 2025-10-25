
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

---
### 6.2.2 Memory layout of a process:
* Every process in memory divided into logical section
	* Stack
	* Heap
	* Data segment
	* Code segment

```
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

---
### 6.2.3 Paging:
* Paging is dividing memory small fixed boxes, equal size small boxed calls pages.
* It will avoid memory waste
* Page -- fixed size block in virtual memory
* Frame -- Physical memory blocks in RAM
* Page table --maps virtual pages --> Physical memory
* It eliminating fragmentation
	* Ensuring every small piece of RAM is used optimally

---
### 6.2.4 Segmentation:
* It divided memory based on logical section of a program
	* It will be in different size, size will be based on logical section value

|Segment|Contains|Example|
|---|---|---|
|**Code Segment**|Instructions|Your program’s logic|
|**Data Segment**|Global/static data|Configuration values|
|**Stack Segment**|Local variables, function calls|Temporary values|
|**Heap Segment**|Dynamically allocated memory|Objects created at runtime|
* There is a chance for external fragmentation
---
### 6.2.5 Virtual memory:
* When RAM is full then OS will use some portion of disk to act as extra memory
	* OS moves less used pages to swap space on disk
	* Active pages stay in RAM
	* When needed again --> swapped back from disk
* Continues swap will lead to down performance --> `thrashing`
---
### 6.2.6 Page table:
* Each process has its own page table, it has
	* Virtual page number
	* Physical page number

|Virtual Page|Physical Frame|
|---|---|
|0|3|
|1|7|
|2|1|
|3|5|

---
### 6.2.7 Swapping
* Moving data between RAM and disk
* when there is not enough memory in RAM then OS temp moves inactive processes pages to disk(swap area), when needed again, it swaps back them
---
