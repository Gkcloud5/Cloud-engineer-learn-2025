## 🚀 WEEK 1 – FastAPI + Python for AI & DevOps

**Goal: Become capable of building real backend APIs for AI & DevOps use cases**

---

## 📅 Day 1 – Core FastAPI Fundamentals (Only What Matters)


### 🎯 Topics to Learn

* FastAPI structure
* Path operations (GET, POST)
* Request & response models (Pydantic basics)
* Running server with Uvicorn
* API docs (Swagger UI)

### 🛠 What to Practice

* Create a basic FastAPI app
* Add 2 endpoints:

  * `/`
  * `/status`
* Return JSON responses
* Test using browser + Swagger

### 🧰 Tools Required

* Python 3.10+
* FastAPI
* Uvicorn
* VS Code

### ✅ Expected Outcome

You can:

* Start a FastAPI server
* Create basic REST APIs
* Understand request/response flow
  This is the **core 20%** that powers everything else.

---

## 📅 Day 2 – Async + Background Tasks + Logging

![Image](https://devopedia.org/images/article/280/2821.1593611212.png)

![Image](https://media.licdn.com/dms/image/v2/D4D12AQGWtc3j7S82AA/article-cover_image-shrink_720_1280/article-cover_image-shrink_720_1280/0/1728674114829?e=2147483647\&t=WP-5JQeuRd34CIId35un-KdP2csUtIaJmCEsVxi4fkc\&v=beta)

![Image](https://mathspp.com/blog/til/042/thumbnail.webp)

![Image](https://images.ctfassets.net/em6l9zw4tzag/4s0fWlp7YWsr4tAP571KPC/265b2967991a65ba8a6448e7f4ecb229/logging-in-python-image11.png?fm=png\&h=707\&q=50\&w=1290)

### 🎯 Topics to Learn

* `async` and `await` (only usage, not theory)
* FastAPI BackgroundTasks
* Environment variables (.env)
* Python logging (structured logs)

### 🛠 What to Practice

* Convert one endpoint to async
* Add background task (e.g., write log to file)
* Load API key from environment variable
* Add proper logging to every request

### 🧰 Tools Required

* python-dotenv
* logging module
* FastAPI BackgroundTasks

### ✅ Expected Outcome

You can:

* Write async endpoints
* Handle background jobs
* Secure API keys properly
* Add production-style logging
  Now your API looks job-ready.

---

# 🔥 Day 3 – Build: Health Check API

### 🎯 Topics

* System status reporting
* JSON response structuring
* Uptime calculation

### 🛠 What to Practice

* Create `/health` endpoint
* Return:

  * status
  * timestamp
  * uptime
* Add logging

### 🧱 What to Build

A production-style health check API.

### 🧰 Tools

* FastAPI
* datetime
* logging

### ✅ Expected Outcome

You can build DevOps-style service monitoring endpoints.
This is used in Kubernetes, Docker, CI/CD.

---

## 📅 Day 4 – Build: CPU Monitoring API

![Image](https://cdn.shopify.com/s/files/1/0329/9865/3996/t/5/assets/python_script_to_monitor_cpu_usage_in_linux-oikRMp.True?v=1707774344)

![Image](https://blog.appsignal.com/_next/image?q=90\&url=%2Fimages%2Fblog%2F2024-07%2Fresponse-times-and-throughput.png\&w=3840)

![Image](https://miro.medium.com/1%2Aw7wIj3e6t8ZQ_DGm8tJ4iA.png)

![Image](https://i.sstatic.net/XM2dB.jpg)

### 🎯 Topics

* psutil basics
* System metrics collection
* Clean JSON API structure

### 🛠 What to Practice

* Install and use `psutil`
* Create `/cpu` endpoint
* Return:

  * CPU %
  * Memory %
  * Disk %

### 🧱 What to Build

A lightweight system monitoring API.

### 🧰 Tools

* psutil
* FastAPI
* logging

### ✅ Expected Outcome

You can expose infrastructure metrics via API.
Very useful for DevOps/backend roles.

---

## 📅 Day 5 – Build: AI Text Summarizer API

![Image](https://fastapi.tiangolo.com/img/tutorial/body/image01.png)

![Image](https://us1.discourse-cdn.com/openai1/original/4X/e/0/3/e03947e9f261d26abc1917db950843b812af62e3.png)

![Image](https://opengraph.githubassets.com/1eb418a966b62ed003159d26c4398289e0702ebaccc093ce37274f8288519a87/avatsaev/av-local-llm-api)

![Image](https://blog.greenflux.us/images/posts/local-llms-and-filemaker-pro/image-7.png)

### 🎯 Topics

* POST request handling
* Calling external API (LLM)
* Handling API keys securely

### 🛠 What to Practice

* Create `/summarize` POST endpoint
* Accept JSON input text
* Call local LLM or OpenAI
* Return summarized result

### 🧱 What to Build

A working AI-powered summarizer backend API.

### 🧰 Tools

* FastAPI
* requests / httpx
* Local LLM API or OpenAI
* dotenv

### ✅ Expected Outcome

You now know how to:

* Integrate AI into backend APIs
* Handle external services
* Build AI microservices

This is highly job-switch valuable.

---

## 📅 Day 6 – Mini Project: DevOps AI Monitoring Microservice

### 🧱 Build This Project

Combine everything:

Endpoints:

* `/health`
* `/cpu`
* `/summarize`
* Logging enabled
* Environment variable config
* Async endpoints
* Background logging task

### 🎯 What to Focus On

* Clean folder structure
* Error handling
* Proper logging
* Clean API documentation

### 🧰 Tools

* FastAPI
* Uvicorn
* psutil
* logging
* dotenv
* local LLM / OpenAI

### 📦 Final Output

A complete backend microservice that:

* Monitors system health
* Exposes metrics
* Integrates AI
* Uses async
* Uses environment variables
* Uses logging

---

# 🎯 End of Week Result (Job-Ready Outcome)

By the end of 6 days, you can:

* Build production-style backend APIs
* Integrate AI models
* Expose DevOps metrics
* Use async properly
* Handle logging and environment configs
* Build deploy-ready microservices

This is the **20% skill set** that gives you 80% readiness for:

* Backend Developer roles
* AI API Engineer roles
* DevOps Automation roles
* Platform Engineer roles


