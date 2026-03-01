
This is a VERY powerful Day 3 plan 🔥  
Now we turn it into a structured **90-minute deep-learning session** made exactly for you.

You said:

- You know a little
    
- Your goal is building projects
    
- Topic: Python + FastAPI + DevOps
    
- Focus: Monitoring API
    

Perfect. We will make this practical and builder-focused 💪

---

# 🚀 90-Minute Learning Plan

## Day 3 – System Monitoring API (DevOps Integration)

---

# ⏱️ FIRST 30 MINUTES – Learn the Foundations (Simple & Clear)

## 1️⃣ What is Monitoring? (5 mins)

Imagine you run a cloud server.

You must know:

- Is CPU overloaded?
    
- Is memory full?
    
- Is system slow?
    

If you don’t monitor:

- App crashes
    
- Server becomes slow
    
- Users complain
    

This is why tools like:

- Prometheus
    
- Grafana
    
- CloudWatch
    

exist.

Today → YOU build a mini monitoring system.

---

## 2️⃣ What is psutil? (10 mins)

![Image](https://bigl.es/content/images/2019/07/Screenshot-from-2019-07-07-21-39-25.png)

![Image](https://i.sstatic.net/ulISM.png)

![Image](https://www.linuxfoundation.org/hs-fs/hubfs/Imported_Blog_Media/memory_2-1.jpeg?height=606&name=memory_2-1.jpeg&width=795)

![Image](https://www.linuxfoundation.org/hs-fs/hubfs/Imported_Blog_Media/memory_5-1.jpeg?height=610&name=memory_5-1.jpeg&width=792)

`psutil` = Python system utility library.

It allows Python to:

- Read CPU usage
    
- Read memory usage
    
- Read disk usage
    
- Read process info
    

It talks to the OS.

Think of it like:  
Python → psutil → Operating System → Hardware

Install:

```bash
pip install psutil
```

---

## 3️⃣ CPU Usage (5 mins)

```python
import psutil

cpu = psutil.cpu_percent(interval=1)
print(cpu)
```

What happens?

- It checks CPU usage for 1 second
    
- Returns percentage
    

Example output:

```
23.5
```

Means 23.5% CPU is used.

---

## 4️⃣ Memory Usage (5 mins)

```python
memory = psutil.virtual_memory()
print(memory.percent)
```

This returns:

- Total memory
    
- Used memory
    
- Free memory
    
- Percent used
    

We only need `.percent`

---

## 5️⃣ Why DevOps Uses This (5 mins)

In real cloud systems:

- Kubernetes checks CPU
    
- Auto-scaling uses CPU %
    
- Alerts trigger when memory > 80%
    

You are building the base of that system.

Now you are thinking like DevOps 👏

---

# ⏱️ NEXT 30 MINUTES – Practice Step by Step

We combine FastAPI + psutil.

## Step 1 – Create File

Create:

```
main.py
```

---

## Step 2 – Basic FastAPI Setup

```python
from fastapi import FastAPI
import psutil
from datetime import datetime

app = FastAPI()
```

---

## Step 3 – Create /cpu Endpoint

```python
@app.get("/cpu")
def get_cpu():
    cpu = psutil.cpu_percent(interval=1)
    return {"cpu_percent": cpu}
```

Test:

```
http://127.0.0.1:8000/cpu
```

---

## Step 4 – Create /memory Endpoint

```python
@app.get("/memory")
def get_memory():
    memory = psutil.virtual_memory().percent
    return {"memory_percent": memory}
```

---

## Step 5 – Create /metrics Endpoint

```python
@app.get("/metrics")
def get_metrics():
    cpu = psutil.cpu_percent(interval=1)
    memory = psutil.virtual_memory().percent
    timestamp = datetime.utcnow()

    return {
        "cpu_percent": cpu,
        "memory_percent": memory,
        "timestamp": timestamp
    }
```

Run server:

```bash
uvicorn main:app --reload
```

Test in browser.

Now you have a monitoring API 🎉

---

# ⏱️ FINAL 30 MINUTES – Mini Project (Real Builder Mode)

Now we upgrade this into a proper mini project.

---

# ✅ CPU Monitoring API – Final Version

We improve 3 things:

1. Add logging
    
2. Make endpoint async
    
3. Clean response structure
    

---

## Add Logging

```python
import logging

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)
```

---

## Final Improved Code

```python
from fastapi import FastAPI
import psutil
from datetime import datetime
import logging

app = FastAPI()

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

@app.get("/metrics")
async def get_metrics():
    cpu = psutil.cpu_percent(interval=1)
    memory = psutil.virtual_memory().percent
    timestamp = datetime.utcnow()

    logger.info(f"CPU: {cpu} | Memory: {memory}")

    return {
        "cpu_percent": cpu,
        "memory_percent": memory,
        "timestamp": timestamp
    }
```

---

# 🧠 What You Just Learned

You now understand:

✔ How backend reads system data  
✔ How DevOps tools gather metrics  
✔ How monitoring APIs work  
✔ How logging works  
✔ How to expose metrics over HTTP

This is the foundation of:

- Prometheus exporters
    
- Cloud monitoring systems
    
- Production observability
    

---

# 🎯 Optional Bonus (If Extra Time)

Add:

- Response model using Pydantic
    
- Dockerize it
    
- Add `/health` endpoint
    
- Return hostname
    

---

# 💡 Challenge Question (Think Like Cloud Engineer)

If CPU becomes 95% for 5 minutes:

- What should system do?
    
- Send alert?
    
- Restart service?
    
- Scale server?
    

Think about it.

---

If you want, tomorrow we can:

- Dockerize this API
    
- Push to cloud
    
- Add Prometheus integration
    
- Deploy using CI/CD
    

You’re not just learning syntax.

You are building cloud thinking 🔥