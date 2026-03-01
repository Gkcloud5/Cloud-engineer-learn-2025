
## What is monitoring?
* If CPU 100% hit then server will be slow and struggle to load the requests
* Request wait in queue and response time increases
* When system is slow need to check
	* CPU usage
	* Memory usage
	* Disk IO
	* network
	* Running processes

### Swap:
* When memory hits 98% then
	* OS starts using swap
	* Disk IO increases
	* System becomes slow
* Memory pressure causing disk thrashing.


## psutils:
* in python we can't get the metrices from OS, OS have system calls to tell the things going on OS like memory, CPU metrics.
* By using psutil, it act as bridge that wraps those system calls in python friendly functions
* Flow is
	* Psutil --> OS kernel --> Hardware counters
* Psutil needs to
	* Talks to OS kernel
	* Use system calls
	* Access low level process and hardware information
* It's `C underneath + python wrapper on top`
```
psutil.cpu_percent()
```

* Flow
```
Python → C extension → system call → kernel → CPU stats → back to Python.
```

```
import psutil
cpu = psutil.cpu_percent(interval=1)
print(cpu)
```

```
memory = psutil.virtual_memory()
print(memory.percent)
```

