

# 🚀 DAY 1 — Docker Core + Running Your FastAPI in Container

## 1️⃣ What to Learn First (Core Basics)

Focus only on these **3 core ideas**:

- **Image vs Container**  
    → Image = blueprint  
    → Container = running app
    
- **Dockerfile = Recipe**  
    → Step-by-step instructions to build your app environment
    
- **Port Mapping**  
    → Container world vs your machine (`-p 8000:8000`)
    

👉 Connect to what you know:  
Your FastAPI app = normal Python app  
Docker = “wrap your app + environment into a portable box”

---

## 2️⃣ What to Practice (Hands-on First)

### 🔥 Task 1: Dockerize your FastAPI app

Create:

**Dockerfile**

```dockerfile
FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

---

### 🔥 Task 2: Build & Run

```bash
docker build -t myfastapi .
docker run -d -p 8000:8000 myfastapi
```

👉 Open:

```
http://localhost:8000
```

---

### 🔥 Task 3: Break & Fix (VERY IMPORTANT)

Try intentionally:

- Remove `COPY . .` → see failure
    
- Change port → see mismatch
    
- Stop container → restart
    

👉 This builds **real understanding**

---

## 3️⃣ What to Build (Mini Project)

### ✅ Version 1:

- FastAPI app with 1 endpoint `/health`
    
- Dockerized
    
- Runs locally
    

### ✅ Version 2:

- Add logging
    
- Add `.env` support
    
- Pass env variables into container
    

```bash
docker run -d -p 8000:8000 --env-file .env myfastapi
```

---

## 4️⃣ Common Mistakes to Prevent

❌ Thinking Docker is VM → it’s NOT  
❌ Forgetting `0.0.0.0` → app won’t be accessible  
❌ Not rebuilding image after code change  
❌ Ignoring logs → always use:

```bash
docker logs <container_id>
```

---

## 5️⃣ How to Test Understanding

Answer these without seeing notes:

- Why does `localhost` not work inside container?
    
- What happens if you don’t expose port?
    
- Difference between:
    
    - `docker run`
        
    - `docker build`
        

👉 If you can explain this simply → Day 1 success ✅

---

# 🚀 DAY 2 — Docker Compose + Nginx + SSL + VPS

This is where things become **real-world production** 🔥

---

## 1️⃣ What to Learn First (Core Basics)

- **Docker Compose = Multi-container manager**
    
- **Nginx = Traffic controller**
    
- **Reverse Proxy = Gateway**
    
- **SSL = HTTPS security layer**
    

👉 Mental model:

```
User → Nginx → FastAPI container
```

---

## 2️⃣ What to Practice

---

### 🔥 Task 1: Docker Compose Setup

**docker-compose.yml**

```yaml
version: "3"

services:
  app:
    build: .
    container_name: fastapi_app
    restart: always

  nginx:
    image: nginx:latest
    container_name: nginx_proxy
    ports:
      - "80:80"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
    depends_on:
      - app
```

---

### 🔥 Task 2: Nginx Reverse Proxy

**nginx.conf**

```nginx
events {}

http {
    server {
        listen 80;

        location / {
            proxy_pass http://app:8000;
        }
    }
}
```

---

### 🔥 Task 3: Run Everything

```bash
docker-compose up -d
```

👉 Now open:

```
http://localhost
```

---

## 3️⃣ What to Build (Mini Production System)

### ✅ Version 1:

- FastAPI container
    
- Nginx container
    
- Works locally via port 80
    

---

### ✅ Version 2: Deploy to VPS

Steps:

1. Buy VPS (or use existing)
    
2. SSH into server
    
3. Install Docker
    

```bash
sudo apt update
sudo apt install docker.io docker-compose -y
```

4. Copy project
    
5. Run:
    

```bash
docker-compose up -d
```

---

### ✅ Version 3: Add SSL (Let’s Encrypt)

Use **Certbot**

```bash
sudo apt install certbot python3-certbot-nginx
```

```bash
sudo certbot --nginx
```

👉 Now your app runs on:

```
https://yourdomain.com
```

---

## 4️⃣ Common Mistakes to Prevent

❌ Trying SSL before domain works  
❌ Forgetting DNS → domain must point to VPS  
❌ Hardcoding IP instead of service name (`app`)  
❌ Not exposing port 80 in VPS firewall

---

## 5️⃣ How to Test Understanding

Explain this clearly:

- Why do we need Nginx if FastAPI already runs?
    
- What happens when user hits your domain?
    
- Why use Docker Compose instead of multiple `docker run`?
    

---

# 🧠 Final Learning Strategy (Important)

Don’t rush.

### Use this cycle:

1. Build → break → fix
    
2. Run commands without copy-paste
    
3. Explain to yourself out loud
    

---

# ⚡ If You Want Next Level

After this 2-day plan, your next steps should be:

- CI/CD (GitHub Actions)
    
- Docker volumes (data persistence)
    
- Monitoring (Prometheus + Grafana)
    

---

If you follow this properly, you’ll jump from:  
👉 “I know Docker”  
to  
👉 “I can deploy production apps”

---

If you want, I can:

- Sit with you step-by-step while you execute
    
- Debug your errors live
    
- Or give you a **real production-level project**
    

Just tell me 👍