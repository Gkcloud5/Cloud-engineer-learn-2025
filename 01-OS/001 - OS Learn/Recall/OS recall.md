# **30 FAANG-Level Operating System Interview Questions**

---

## 🧠 **Section 1: Core OS Fundamentals (Warm-up / Screening Level)**

1. **What happens when you turn on your computer, step-by-step from power-on to desktop screen?**  
    🔍 _Tests:_ System boot process, OS loading, kernel initialization, and process startup.
    
2. **Explain the difference between a process and a thread — and why threads are faster.**  
    🔍 _Tests:_ Understanding of context switching, memory sharing, and overhead.
    
3. **What’s the difference between a monolithic kernel and a microkernel? Which one scales better?**  
    🔍 _Tests:_ Architectural understanding and design trade-offs.
    
4. **Describe how system calls work. What happens in the OS when you call `read()` or `write()`?**  
    🔍 _Tests:_ User mode ↔ kernel mode transitions, and OS–hardware boundary.
    
5. **Explain what happens when you execute a program (like `./a.out`) on Linux.**  
    🔍 _Tests:_ Process creation, `fork()`, `exec()`, loading program into memory, and scheduling.
    

---

## ⚙️ **Section 2: Process & Thread Management**

6. **What’s stored in a Process Control Block (PCB)?**  
    🔍 _Tests:_ Knowledge of context switching, process state, CPU registers, scheduling info.
    
7. **How does the OS perform a context switch? What data must it save and restore?**  
    🔍 _Tests:_ Thread stack, CPU state, registers, process memory space.
    
8. **What are zombie and orphan processes? How can you prevent them?**  
    🔍 _Tests:_ Process lifecycle management, parent-child relationships, `wait()`.
    
9. **Why is `fork()` followed by `exec()` used in UNIX systems?**  
    🔍 _Tests:_ Process creation pipeline and performance design.
    
10. **If two threads share the same address space, how do they communicate safely?**  
    🔍 _Tests:_ Concurrency, synchronization primitives (locks, semaphores, condition variables).
    

---

## 🧮 **Section 3: CPU Scheduling & Performance**

11. **What’s the difference between preemptive and non-preemptive scheduling?**  
    🔍 _Tests:_ Process interruption logic and fairness trade-offs.
    
12. **You have 3 processes with burst times 5, 3, and 8. Which scheduling algorithm gives minimum waiting time? Why?**  
    🔍 _Tests:_ Algorithmic reasoning (SJF vs FCFS vs RR).
    
13. **Why is Round Robin used in modern systems even though it’s not always the fastest?**  
    🔍 _Tests:_ Understanding of fairness and time-sharing in multi-user systems.
    
14. **How does CPU scheduling affect system responsiveness and throughput?**  
    🔍 _Tests:_ Real-world optimization thinking.
    
15. **What’s the difference between throughput, turnaround time, and waiting time? Give formulas.**  
    🔍 _Tests:_ Performance metrics understanding.
    

---

## 🧵 **Section 4: Synchronization & Deadlocks**

16. **What is a race condition, and how can you avoid it in multi-threaded code?**  
    🔍 _Tests:_ Concurrency safety, atomic operations, critical sections.
    
17. **Explain the four necessary conditions for a deadlock. Can a system avoid it entirely?**  
    🔍 _Tests:_ Coffman conditions, theoretical understanding.
    
18. **How does a semaphore differ from a mutex? Give a real-world example for each.**  
    🔍 _Tests:_ Synchronization primitives and practical analogy.
    
19. **Describe how you would detect a deadlock in a system. What’s the complexity of detection?**  
    🔍 _Tests:_ Resource allocation graph, cycle detection.
    
20. **If you were to design a deadlock prevention system, which Coffman condition would you break first and why?**  
    🔍 _Tests:_ Analytical reasoning and trade-off thinking.
    

---

## 💾 **Section 5: Memory Management & Virtualization**

21. **What is the difference between paging and segmentation? Which one avoids external fragmentation?**  
    🔍 _Tests:_ Memory structure and fragmentation concepts.
    
22. **Explain how virtual memory works. Why do we need it even on systems with lots of RAM?**  
    🔍 _Tests:_ Abstraction, isolation, and performance optimization.
    
23. **What’s a page fault? What steps does the OS take to handle it?**  
    🔍 _Tests:_ Demand paging, disk access latency, page replacement.
    
24. **Explain the difference between stack and heap memory. Why does the stack grow downward?**  
    🔍 _Tests:_ Program memory layout.
    
25. **How does the OS translate a virtual address to a physical address?**  
    🔍 _Tests:_ Page tables, TLB, and MMU (Memory Management Unit).
    

---

## 📂 **Section 6: File Systems & I/O**

26. **Explain how inodes work in Linux. What information is stored inside an inode?**  
    🔍 _Tests:_ Low-level understanding of file systems.
    
27. **What’s the difference between buffering, caching, and spooling? Give an example for each.**  
    🔍 _Tests:_ Data flow and I/O optimization.
    
28. **How does the OS handle interrupts from I/O devices?**  
    🔍 _Tests:_ Interrupt handling mechanism, CPU scheduling interplay.
    
29. **What’s the role of a device driver? Why can bad drivers crash the OS?**  
    🔍 _Tests:_ Kernel-space code and privilege awareness.
    
30. **Explain how file permissions work in UNIX. What does `chmod 755` mean exactly?**  
    🔍 _Tests:_ Permission bits, user/group/others model.
    

---

## 🔒 **Section 7: Security, Reliability & Design Thinking**

31. **Explain the difference between authentication, authorization, and accounting (AAA model).**  
    🔍 _Tests:_ Core security flow understanding.
    
32. **How does OS isolation prevent one process from reading another’s memory?**  
    🔍 _Tests:_ Hardware memory protection and virtual memory.
    
33. **What’s the difference between a kernel panic and a user-space crash?**  
    🔍 _Tests:_ Privilege boundaries and failure domains.
    
34. **How does Linux enforce access control for system files?**  
    🔍 _Tests:_ File permissions, ownership, and process privileges.
    
35. **If you were designing an OS for cloud infrastructure, what changes would you make to improve security and concurrency?**  
    🔍 _Tests:_ System design mindset — creativity + technical reasoning.
    

---

# ⚡ **Bonus FAANG-Style Rapid Fire (for deeper interviews)**

These questions test how well you **connect concepts** — a FAANG favorite.

36. **What happens inside the OS when you type a command and press Enter in a terminal?**
    
37. **Why is context switching expensive, and how do threads help reduce this cost?**
    
38. **What is thrashing, and how can you detect and fix it?**
    
39. **Why does the OS prefer paging over segmentation in modern systems?**
    
40. **What’s the difference between kernel threads and user threads?**