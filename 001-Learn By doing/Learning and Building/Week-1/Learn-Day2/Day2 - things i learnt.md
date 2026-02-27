
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
* If client sends request then endpoint will run, if error occurs then exception will be raised and exception will hanlde it and customer response will be returned
* Catches exception and sends clean and structured reponse to the client

```
An **exception handler** works when a client sends a request and the endpoint starts running. If an error happens during execution, Python raises an exception. The exception handler catches that error and prevents the app from crashing. Instead of showing a raw error, it returns a clean and structured response to the client. This helps send proper status codes and clear error messages. It improves API reliability and user experience. Without it, users may see confusing or unsafe error details. Exception handling makes the system stable and professional.
```

## load dotenv:
