# 🚀 **3-Hour Focused Study Plan — Day 1 FastAPI Fundamentals**

## ⏱️ Total Time: 3 Hours

Structure:

✅ 45 min — Core understanding
✅ 60 min — Hands-on practice
✅ 45 min — Mini build (Health API)
✅ 30 min — Testing + review + output

Goal → **Working FastAPI health check service**

---

# 🧠 **Phase 1 — Understand Core Concepts (45 mins)**

## 🎯 Goal

Understand how backend APIs work + what FastAPI does.

No memorization. Just clarity.

---

## ✅ Learn These Concepts (Simple Understanding)

### 1️⃣ What is FastAPI (10 mins)

Understand:

* FastAPI = tool to build backend APIs using Python
* Used in AI apps because:

  * very fast
  * auto documentation
  * validation built-in
  * easy to connect AI models

👉 Think:

> FastAPI = Python server that receives requests and returns data.

Example:

```
Browser → request → FastAPI → response
```

---

### 2️⃣ How API Structure Works (15 mins)

Learn only these:

### GET → fetch data

```
/health → returns status
```

### POST → send data

```
send JSON → server processes → response
```

Understand:

* endpoint = URL path
* function = logic

---

### 3️⃣ Path vs Query Parameters (10 mins)

Understand difference:

```
/user/10 → path parameter
/status?name=gokul → query parameter
```

---

### 4️⃣ Pydantic Basics (10 mins)

Simple idea:

> Pydantic validates request data automatically.

Example:

```
client sends data → FastAPI checks format → accept/reject
```

Just understand purpose.

---

## ✅ Quick Learning Resources (optional)

* FastAPI official tutorial → First 3 sections only
* Search: "FastAPI 10 minute tutorial"

**Do not go deep. Move to practice fast.**

---

# 💻 **Phase 2 — Hands-On Practice (60 mins)**

## 🎯 Goal

Struggle with setup + understand project structure.

---

## ✅ Step 1 — Environment Setup (15 mins)

Install:

```
pip install fastapi uvicorn
```

Create project:

```
fastapi-day1/
 ├── main.py
```

---

## ✅ Step 2 — First FastAPI App (15 mins)

Write:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def home():
    return {"message": "Hello FastAPI"}
```

Run:

```
uvicorn main:app --reload
```

Open:

```
http://127.0.0.1:8000
http://127.0.0.1:8000/docs
```

👉 Learn:

* auto reload
* Swagger UI

---

## ✅ Step 3 — Create Required Endpoints (20 mins)

Add:

```
/health
/status?name=gokul
```

Try yourself first.

If stuck:

```python
@app.get("/health")
def health():
    return {"status": "ok"}

@app.get("/status")
def status(name: str):
    return {"message": f"Hello {name}"}
```

---

## ✅ Step 4 — First POST with Pydantic (10 mins)

Add model:

```python
from pydantic import BaseModel

class User(BaseModel):
    name: str
    age: int

@app.post("/user")
def create_user(user: User):
    return {"received": user}
```

Test in Swagger UI.

---

# 🏗️ **Phase 3 — Mini Build (45 mins)**

## 🎯 Goal

Build something real → Health Check API.

---

## ✅ Build This Small Backend Service

Create clean structure:

```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI(title="Health API", version="1.0")
```

---

## Required Endpoints

### ✅ `/health`

```
{
  "status": "ok"
}
```

---

### ✅ `/version`

```
{
  "version": "1.0"
}
```

---

### ✅ `/status?name=gokul`

Return greeting.

---

### ✅ `/user` POST with validation

---

## ⭐ Extra Challenge (if time)

Add:

```
server_time endpoint
```

(Hint: `datetime` module)

---

# 🔍 **Phase 4 — Testing + Deep Understanding (30 mins)**

## 🎯 Goal

Understand what you built.

---

## ✅ Test Everything (15 mins)

Use:

```
http://127.0.0.1:8000/docs
```

Try:

* missing parameters
* wrong data types
* correct data

Observe validation errors.

This builds real backend intuition.

---

## ✅ Review What You Learned (15 mins)

Answer these:

* What happens when browser hits endpoint?
* What is GET vs POST?
* Why use Pydantic?
* What does Uvicorn do?

If you can explain → success.

---

# ✅ **Final Output of Today (Must Complete)**

By end of 3 hours you should have:

```
✔ Running FastAPI server
✔ /health endpoint
✔ /version endpoint
✔ /status query parameter endpoint
✔ POST request with validation
✔ Tested via Swagger
```

This is your **first production-style backend foundation**.

---

# 🧩 What You Should Feel After Session

If session worked correctly you will feel:

✅ APIs no longer scary
✅ Backend flow makes sense
✅ You can run a service
✅ You understand request → response cycle
✅ You have working code

That’s the goal.
