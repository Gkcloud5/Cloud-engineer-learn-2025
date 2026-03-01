# 🚀 90-Minute Learning Plan

## Day 3 – System Monitoring API (DevOps Integration)

---

# ⏱️ FIRST 30 MINUTES – Learn the Foundations (Simple & Clear)

## 1️⃣ What is Monitoring? (5 mins)

Imagine you run a cloud server.

You must know:

* Is CPU overloaded?
* Is memory full?
* Is system slow?

If you don’t monitor:

* App crashes
* Server becomes slow
* Users complain

This is why tools like:

* Prometheus
* Grafana
* CloudWatch

exist.

Today → YOU build a mini monitoring system.

---

## 2️⃣ What is psutil? (10 mins)


`psutil` = Python system utility library.

It allows Python to:

* Read CPU usage
* Read memory usage
* Read disk usage
* Read process info

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

* It checks CPU usage for 1 second
* Returns percentage

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

* Total memory
* Used memory
* Free memory
* Percent used

We only need `.percent`

---

## 5️⃣ Why DevOps Uses This (5 mins)

In real cloud systems:

* Kubernetes checks CPU
* Auto-scaling uses CPU %
* Alerts trigger when memory > 80%

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

* Prometheus exporters
* Cloud monitoring systems
* Production observability

---

# 🎯 Optional Bonus (If Extra Time)

Add:

* Response model using Pydantic
* Dockerize it
* Add `/health` endpoint
* Return hostname

---

# 💡 Challenge Question (Think Like Cloud Engineer)

If CPU becomes 95% for 5 minutes:

* What should system do?
* Send alert?
* Restart service?
* Scale server?

Think about it.

