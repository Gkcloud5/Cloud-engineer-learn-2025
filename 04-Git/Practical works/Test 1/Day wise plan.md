# **DAY 1 — Understand + Build Foundation (VPS Version)**

Goal:  
✔ Understand concepts  
✔ Build simple app  
✔ Learn Docker  
✔ Set up **VPS environment + registry (GHCR)**  
✔ Add GitHub Secrets

---

## **1️⃣ Understand the big picture (1 hour)**

### You learn:

- What CI/CD means
    
- What GitHub Actions automates
    
- What Docker images & containers are
    
- What a registry is (GitHub Container Registry)
    
- What deployment looks like on a VPS (SSH → pull image → run container)
    

### Outcome:

You understand **why the pipeline is:**  
**build → scan → push → deploy to VPS**

---

## **2️⃣ Build a tiny “Hello World” app (1 hour)**

Choose any language (Node.js recommended).  
Goal: simple Hello World in browser.

Run locally:

`npm install npm start`

### Outcome:

A working mini web app served on **localhost:8080**

---

## **3️⃣ Learn Docker basics + create Dockerfile (1 hour)**

You learn:

- What a container is
    
- How Docker packages your app
    
- What `docker build` does
    
- How to run your app inside Docker
    

Tasks:

- Write a Dockerfile
    
- Build image locally
    
- Run container
    

Example:

`docker build -t hello-cicd:local . docker run -d -p 8080:8080 hello-cicd:local`

### Outcome:

Your app runs **inside Docker**, same way it will run on your VPS.

---

## **4️⃣ Set up your VPS environment (2 hours)**

_(This replaces the entire Cloud Run + Artifact Registry setup)_

### ✔ Install Docker on VPS

`curl -fsSL https://get.docker.com | sh`

### ✔ Create a deploy user

`sudo adduser deployuser sudo usermod -aG docker deployuser`

### ✔ Set up SSH key-based access

Generate a key on your local machine:

`ssh-keygen -t ed25519 -f ~/.ssh/github_actions_key`

Copy public key to VPS:

`ssh-copy-id -i ~/.ssh/github_actions_key.pub deployuser@VPS_IP`

### ✔ Choose a container registry

You need somewhere to store built Docker images.

**Recommended: GitHub Container Registry (GHCR)**  
No need to use Docker Hub or cloud registries.

### ✔ Add GitHub Secrets

In repo → Settings → Secrets → Actions:

You add:

- `VPS_SSH_KEY` → contents of private key `github_actions_key`
    
- `VPS_HOST` → your VPS IP
    
- `VPS_USER` → deployuser
    
- `VPS_SSH_PORT` → 22 (or your custom port)
    
- `GHCR_TOKEN` → GitHub PAT with `write:packages`
    

### Outcome:

✔ VPS can accept deploys  
✔ Registry is ready  
✔ GitHub Secrets prepared

---

# ✔️ **End of Day 1 Result**

By end of Day 1 you have:

- Clear understanding of CI/CD
    
- A working app
    
- A working Docker image
    
- A VPS ready for deployment
    
- GitHub Secrets ready for CI/CD pipeline
    

This is the perfect foundation for Day 2.

---

# 🗓️ **DAY 2 — Build the CI/CD Pipeline + Deploy to VPS**

Goal:  
✔ Build pipeline  
✔ Push image to GHCR  
✔ Scan code  
✔ SSH into VPS and deploy container  
✔ Verify live app

---

## **1️⃣ Create GitHub Actions workflow (2 hours)**

Stages:

### ✓ **Build**

- checkout code
    
- build Docker image
    
- push to GitHub Container Registry (GHCR)
    

### ✓ **Scan**

- run CodeQL or Trivy security scan
    

### ✓ **Deploy (VPS)**

- SSH into VPS
    
- pull new image
    
- restart Docker container
    

### Outcome:

You now have **cicd-vps.yml** in `.github/workflows`.

---

## **2️⃣ Run the pipeline (1 hour)**

Do this:

1. Push code → GitHub Actions triggers
    
2. Watch workflow:
    
    - Build
        
    - Scan
        
    - Deploy to VPS
        

### Outcome:

The pipeline is working end-to-end.

---

## **3️⃣ Verify deployment (30 minutes)**

Go to your VPS:

`docker ps docker logs hello-cicd`

Visit:

`http://YOUR_VPS_IP:8080`

You should see:  
**Hello from VPS CI/CD demo!**

### Outcome:

Live deployment is successful.

---

## **4️⃣ Debug & understand logs (30 minutes)**

Learn:

- Where GitHub logs are
    
- Why build may fail
    
- Why deploy may fail
    
- How to fix common issues
    

This makes your DevOps skills much stronger.

---

# ✔️ **End of Day 2 Result**

You now have:

✔ A working CI/CD pipeline from GitHub → VPS  
✔ Auto build + scan + deploy on every commit  
✔ Dockerized app  
✔ Real deployment automation  
✔ Portfolio-ready real-world DevOps project

---

# 🎉 Final Outcome (after 2 days)

You will know:

- GitHub Actions end-to-end
    
- Docker packaging + registries
    
- Automated deployment to VPS
    
- How to design real DevOps pipelines
    
- How build → scan → push → deploy works at companies