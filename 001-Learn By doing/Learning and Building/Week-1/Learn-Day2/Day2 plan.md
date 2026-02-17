# **3-Hour Deep Work Plan — Day 2: Async + Environment + Logging (Production Basics)**

**Mission:** Make your FastAPI app production-aware, traceable, and environment-driven.

You will:

* understand async practically
* handle environment variables
* implement production logging
* upgrade your Health API

No passive learning. Everything ends in execution.

---

# **0 → 1: Setup (5 minutes — strict)**

Do immediately.

```bash
pip install fastapi uvicorn python-dotenv
```

Project structure (create if missing):

```
project/
 ├── main.py
 ├── .env
 └── logs/
```

Create `.env`:

```
APP_NAME=Production Health API
APP_VERSION=1.0.0
```

---

# **1 hour 15 min — CORE FUNDAMENTALS (Execution Knowledge Only)**

## **0–20 min — Async/Await (Only What You Need)**

### What You Must Understand

* **sync = blocking**
* **async = non-blocking**
* API handles multiple requests → async improves performance for I/O work.

### Mental Model

```
sync → one task waits
async → task pauses, others run
```

### When To Use Async in APIs

Use async when:

* calling database
* external API
* file I/O
* waiting operations

Do NOT use async for:

* heavy CPU work.

### Execution Task (Mandatory)

Create this in `main.py`:

```python
from fastapi import FastAPI
import asyncio

app = FastAPI()

@app.get("/sync")
def sync_test():
    import time
    time.sleep(2)
    return {"message": "sync done"}

@app.get("/async")
async def async_test():
    await asyncio.sleep(2)
    return {"message": "async done"}
```

Run:

```
uvicorn main:app --reload
```

Open 3 browser tabs → hit `/sync` then `/async`.

**Observe response behavior.**
If you don’t test — you failed this block.

---

## **20–45 min — Environment Variables (.env)**

### Why Production Systems Use Env Variables

* no secrets in code
* config changes without code change
* different staging/production behavior

### Core Concept

```
Code → reads configuration from environment
```

### Implementation

Add to `main.py`:

```python
from dotenv import load_dotenv
import os

load_dotenv()

APP_NAME = os.getenv("APP_NAME")
APP_VERSION = os.getenv("APP_VERSION")
```

Test:

```python
@app.get("/env-test")
def env_test():
    return {"app": APP_NAME, "version": APP_VERSION}
```

Run → verify values from `.env`.

If it returns `None` → debug immediately.

---

## **45–75 min — Production Logging (DevOps Level Basics)**

### Why Logging Matters (Operational View)

Production reality:

* systems fail
* users complain
* you need trace
* logs = system memory

Without logs → blind debugging.

### What Production Logs Track

* request received
* execution time
* errors
* system state

### Python Logging Setup

Create this in `main.py`:

```python
import logging

logging.basicConfig(
    level=logging.INFO,
    format="%(asctime)s | %(levelname)s | %(message)s",
    handlers=[
        logging.FileHandler("logs/app.log"),
        logging.StreamHandler()
    ]
)

logger = logging.getLogger(__name__)
```

Test logging:

```python
@app.get("/log-test")
def log_test():
    logger.info("Test log triggered")
    return {"status": "logged"}
```

Confirm file:

```
logs/app.log
```

If no file → fix before moving.

---

# **45 minutes — HARD PRACTICE (No Copy-Paste Thinking)**

You must solve these yourself.

---

## **Challenge 1 — Convert Endpoint to Async (15 min)**

Create endpoint:

```
/process
```

Requirements:

* simulate 3-second operation
* must use async
* log start and finish

Expected thinking:

```
How do I measure execution time?
How do I await delay?
```

Hint (not solution):

```
time.time()
await asyncio.sleep()
```

---

## **Challenge 2 — Request Logging Middleware (15 min)**

Goal:

Log every request automatically.

Log:

* request path
* method
* execution time

You must research **only FastAPI middleware syntax** (max 5 min research).

Then implement.

---

## **Challenge 3 — Error Logging (15 min)**

Create endpoint:

```
/error
```

* intentionally raise exception
* catch it
* log error
* return safe response

Think:

```
try / except
logger.error()
```

---

# **1 Hour — MINI PROJECT (Real Production Upgrade)**

## **Mission: Production Health API v2**

Build from scratch. Do not modify earlier messy code.

Create clean structure inside `main.py`.

---

## **Project Requirements**

### 1️⃣ Health Endpoint

```
GET /health
```

Returns:

```
status
app name (env)
timestamp
```

Must log:

* request
* response

---

### 2️⃣ Info Endpoint (Environment Driven)

```
GET /info
```

Returns:

```
app name
version
environment (add ENV=dev in .env)
```

---

### 3️⃣ Global Request Logging

Every request logs:

```
method
path
execution time
```

---

### 4️⃣ Error Handling + Logging

Any failure → logged.

---

### 5️⃣ Structured Log Message Format

Logs must look like:

```
2026-01-01 12:00 | INFO | GET /health | 32ms
```

---

### Build Order (Strict)

1. logging setup
2. env loading
3. middleware logging
4. health endpoint
5. info endpoint
6. error handler

No skipping order.

---

# **FINAL DELIVERABLE (Definition of Done)**

You have:

✅ `.env` file controlling app behavior
✅ FastAPI app using async endpoint
✅ middleware logging every request
✅ error logging
✅ `/health` endpoint
✅ `/info` endpoint using env variables
✅ log file generated in `/logs`
✅ execution time logged

If any missing → not complete.

---

# **SELF-EVALUATION CHECKLIST (Skills Tested)**

You should confidently answer YES:

* I know when async should be used in APIs.
* I can convert sync → async myself.
* I can load environment variables without guide.
* I can implement logging from scratch.
* I understand why production systems need logs.
* I can measure execution time.
* I can log errors properly.
* I built middleware without copying full tutorial.

Score yourself honestly.

---

# **3 Reflection Questions**

1. What parts forced real thinking vs copy-paste?
2. Where did I struggle most — async, logging, or middleware?
3. If this ran in production, what would still be risky?

Write answers.

---

# **Next Difficulty Upgrade (Mandatory Progression)**

**Day 3 Upgrade → Production Middleware + Request IDs**

Add:

* unique request ID for every request
* include ID in logs
* correlation between logs
* centralized error handler

This is real production backend behavior.



