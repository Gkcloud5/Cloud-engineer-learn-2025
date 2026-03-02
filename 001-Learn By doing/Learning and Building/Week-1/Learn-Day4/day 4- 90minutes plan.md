# 🚀 Day 4 – Build AI API (Text Summarizer)

Total: **105 Minutes Structured Learning**

---

# 🟢 FIRST 45 MINUTES – Learn the Foundations

## 1️⃣ What is an External API? (10 mins)

Simple meaning:

> Your app asks another app to do work and returns the result.

Example:
Your FastAPI server → sends text → OpenAI → gets summary → returns to user.

Flow:

Client → Your API → OpenAI API → Your API → Client

Important understanding:

* Your backend is middleman
* AI does heavy thinking
* You control input/output

---

## 2️⃣ What is an API Key? (10 mins)

API Key = Password to access AI service.

⚠ Never hardcode it like this:

```python
api_key = "sk-123456"
```

Instead use environment variables.

Why?

Because:

* Safe
* Professional
* Production-ready

You will use:

* `python-dotenv`
* `.env` file
* `os.getenv()`

---

## 3️⃣ How Error Handling Works (10 mins)

Things that can fail:

* User sends empty text
* API key missing
* OpenAI server down
* Internet problem

We must:

* Catch errors
* Return clean message
* Not crash the server

Using:

```python
try:
    something()
except Exception as e:
    return error
```

---

## 4️⃣ Response Validation (5 mins)

We must ensure:

* AI actually returned something
* Response is not None
* Response has summary text

Never blindly trust external API.

---

## 5️⃣ Logging & Response Time (10 mins)

Professional backend must log:

* Request received
* Processing started
* Response sent
* Time taken

Why?

In production:
If slow → check logs
If failed → check logs

Use:

```python
import logging
import time
```

Measure time:

```python
start = time.time()
end = time.time()
```

---

# 🟡 NEXT 30 MINUTES – Practice Step-by-Step

Now we practice small pieces.

---

## Step 1 – Install Packages

```bash
pip install fastapi uvicorn openai python-dotenv
```

---

## Step 2 – Create .env File

```
OPENAI_API_KEY=your_key_here
```

---

## Step 3 – Load Environment Variable

Practice:

```python
from dotenv import load_dotenv
import os

load_dotenv()

api_key = os.getenv("OPENAI_API_KEY")
print(api_key)
```

If prints → good.

---

## Step 4 – Create Basic POST Endpoint

Practice creating:

```python
@app.post("/summarize")
```

Accept:

```json
{
  "text": "long paragraph"
}
```

---

## Step 5 – Add Validation

If text is empty:

Return:

```json
{
  "error": "Text cannot be empty"
}
```

---

## Step 6 – Call localLLM model or API

Send text.
Receive summary.
Print it first.
Then return it.

---

## Step 7 – Add Try / Except

Simulate error:

* Remove API key
* See what happens
* Handle properly

---

# 🔴 FINAL 30 MINUTES – Build Mini Project

Now we combine everything.

---

# 🏗 Project: Simple Text Summarizer API

## Features:

✔ Input text
✔ Output summary
✔ API key from env
✔ Logs request
✔ Logs response time
✔ Handles errors
✔ Clean JSON response

---

## Final Structure

```
project/
 ├── main.py
 ├── .env
 ├── requirements.txt
```

---

## Expected API Flow

1. User sends text
2. Validate text
3. Start timer
4. Call OpenAI
5. Validate response
6. Stop timer
7. Log time
8. Return summary

---

## Expected Output Example

Request:

```json
{
  "text": "Artificial intelligence is transforming the world..."
}
```

Response:

```json
{
  "summary": "AI is changing industries by automating and improving processes.",
  "response_time": "0.89 seconds"
}
```




