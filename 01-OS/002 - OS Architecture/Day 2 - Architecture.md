

### How OS communicates with hardware?

*  In this communication process OS has 3 important things
	* Shell
	*  System call
	* Kernel

**User talks to shell and shell tell kernel to do a work with system call, finally kernel take care the task and complete with resources like CPU, Memory, IO device, device manager, security**

---
### 2.1 Shell:
* How we interact with OS.
* It takes our command and send them to the kernel
* **Type:**
	* CLI - text based
	* GUI - Click based interface

-----
### 2.2  Kernel:
* Brain of OS
* **What it does:**
	* Manage processes
	* Controls memory
	* Handles files and devices
	* Security and protection
* Example:
	* CPU scheduling
	* Memory allocation
* Without kernel computer would only handle one job at a time

---
### 2.3  System calls:
* It's translator between apps and kernel
* it's communication channel shell to kernel

| Category          | Example                       | Purpose                     |
| ----------------- | ----------------------------- | --------------------------- |
| Process Control   | `fork()`, `exec()`            | Create and run new programs |
| File Management   | `open()`, `read()`, `write()` | Handle file operations      |
| Device Management | `ioctl()`                     | Control hardware devices    |
| Information       | `getpid()`                    | Get process information     |

---
### 2.4  Monolithic vs Microkernel:
| Feature      | Monolithic Kernel                        | Microkernel                                      |
| ------------ | ---------------------------------------- | ------------------------------------------------ |
| 🧩 Structure | All OS services inside one large kernel  | Only essential parts in kernel; rest run outside |
| ⚡ Speed      | Faster (less communication)              | Slower (more message passing)                    |
| 🔒 Stability | Less safe — one bug can crash the system | Safer — services isolated                        |
| 💻 Example   | Linux, Unix                              | MINIX, QNX, macOS (Hybrid)                       |
* Monolithic kernel -- who does everything himself
* Microkernel -- Team of experts

----

### 2.5  User Mode vs Kernel Mode:
* 