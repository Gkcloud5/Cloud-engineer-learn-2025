
## Things:
1. python async
2. exception handler
3. load_dotnev
4. logg
5. middleware


## python async function:
* in async function is kind of process execution in parallel but it's not, it's doing like if any function is waiting for IO device then that moment CPU is idle so without wasting that async function will push another process in CPU time and utilize it. so it will look like all the process are executing parelley

#### Corrected output:
```
An **async function** in Python does not run code in true parallel like multiple CPUs. It runs in a single thread using an **event loop**. When a task is waiting for I/O (like network call, file read, database query), it does not block the CPU. Instead, it gives control back to the event loop, and the loop runs another ready task. This way, CPU time is not wasted. It looks like tasks are running in parallel, but actually they are switching very fast. Async is best for I/O-bound work, not CPU-heavy work. For CPU-heavy tasks, we use multiprocessing. This makes programs faster and more efficient.
```

## Exception handler:

