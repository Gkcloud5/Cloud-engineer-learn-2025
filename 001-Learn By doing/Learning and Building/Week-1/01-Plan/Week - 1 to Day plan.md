# 🚀 WEEK 1 – FastAPI for GenAI + DevOps (Job-Focused Plan)

---

## ✅ Day 1 – Core FastAPI Fundamentals (Only What Matters)

### Topics to Learn

* What is FastAPI & why it’s used in AI backends
* API structure (GET, POST)
* Path & query parameters
* Request & response models (Pydantic basics)
* Running app with Uvicorn

(We skip unnecessary deep Python theory)

### What to Practice

* Create a basic FastAPI app
* Add:

  * `/`
  * `/health`
  * `/status?name=gokul`
* Use Pydantic model for POST request

### What to Build

✅ Basic Health Check API

Example endpoints:

* `/health` → returns status ok
* `/version` → returns app version

### Tools Required

* Python 3.10+
* FastAPI
* Uvicorn
* VS Code

### Expected Outcome

You understand:

* How APIs are structured
* How backend services respond
* How to run and test APIs (Swagger UI)

This is real backend foundation.

---

## ✅ Day 2 – Async + Environment + Logging (Production Basics)

### Topics to Learn

* What is async/await (practical understanding only)
* When to use async in APIs
* Environment variables (.env)
* Python logging basics
* Why logging matters in DevOps

### What to Practice

* Convert one endpoint to async
* Create `.env` file and load variables
* Add structured logging to endpoints
* Log:

  * API request
  * Errors
  * Execution time

### What to Build

Upgrade Health API:

* Log every request
* Use environment variable for app name
* Add `/info` endpoint using env variables

### Tools Required

* python-dotenv
* logging module
* FastAPI

### Expected Outcome

You now write:

* Production-style backend code
* Environment-aware applications
* Logged and traceable APIs

This is what recruiters expect.

---

## ✅ Day 3 – System Monitoring API (DevOps Integration)

### Topics to Learn

* psutil basics
* CPU usage
* Memory usage
* Why monitoring matters in cloud systems

### What to Practice

* Install psutil
* Create endpoints:

  * `/cpu`
  * `/memory`
  * `/metrics`

### What to Build

✅ CPU Monitoring API

Return:

* CPU %
* Memory %
* Timestamp

Bonus:

* Add logging
* Make endpoint async

### Tools Required

* psutil
* FastAPI
* logging

### Expected Outcome

You now understand:

* Backend + System metrics
* How DevOps tools gather data
* How monitoring APIs work

You’re thinking like a Cloud Engineer.

---

## ✅ Day 4 – Build AI API (Text Summarizer)

### Topics to Learn

* Calling external API (OpenAI or local LLM)
* Handling API keys securely
* Error handling
* Response validation

### What to Practice

* Create POST `/summarize`
* Accept input text
* Return summary
* Handle:

  * Empty text
  * API failure

### What to Build

✅ Simple Text Summarizer API

Structure:

* Input: text
* Output: summary
* Logs request + response time
* API key via environment variable

### Tools Required

* OpenAI API or local LLM
* FastAPI
* python-dotenv
* logging

### Expected Outcome

You now:

* Build GenAI backend
* Secure API keys
* Integrate AI into production APIs

This is job-ready GenAI backend skill.

---

## ✅ Day 5 – Mini Production API Project (Combine Everything)

### Project: AI Monitoring Microservice

### Build:

Single FastAPI app with:

* `/health`
* `/cpu`
* `/memory`
* `/summarize`
* Logging enabled
* Environment-based config
* Async endpoints

Add:

* Error handling
* Clean folder structure:

  ```
  app/
    main.py
    routes/
    services/
    utils/
  ```

### Tools Required

* FastAPI
* psutil
* OpenAI/local LLM
* logging
* dotenv

### Expected Outcome

You now have:

* A real microservice
* AI + DevOps combined
* Proper structure

This is resume-worthy.

---

## ✅ Day 6 – Make It Deploy-Ready (Critical for Job Switch)

### Topics to Learn

* Docker basics
* Writing Dockerfile
* Running FastAPI in container
* Exposing port
* Why containers matter in cloud

### What to Practice

* Write Dockerfile
* Build image
* Run container locally
* Test endpoints

### What to Build

✅ Dockerized AI Monitoring Service

Optional Bonus:

* Push to DockerHub
* Add README

### Tools Required

* Docker
* FastAPI project
* Terminal

### Expected Outcome

You now:

* Understand containerization
* Can deploy backend
* Have a cloud-ready project

This is what makes you employable.

---

# 🎯 End of Week Result

After 6 days (2–3 hrs daily), you will:

✅ Build production-style FastAPI services
✅ Understand async basics
✅ Use logging properly
✅ Integrate AI APIs
✅ Build monitoring endpoints
✅ Dockerize your application

You officially move from:
Beginner → Backend + GenAI + DevOps starter level.


