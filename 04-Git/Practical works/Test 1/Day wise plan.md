# 🗓️ **DAY 1 — Understand + Build Foundation**

Goal:  
✔ Understand concepts  
✔ Build a simple app  
✔ Learn Docker  
✔ Set up cloud + registry

---

## **1️⃣ Understand the big picture (1 hour)**

You learn:

- What is CI/CD
- What GitHub Actions does
- What a Docker image is
- What a Cloud registry is
- What Cloud Run (or similar) is

Outcome:  
You clearly understand **why** we are doing build → scan → deploy.

---

## **2️⃣ Build a tiny “Hello World” app (1 hour)**

Pick any language (Node, Python, Go).  
Goal is just:  
**“Hello World” in browser → running locally.**

Outcome:  
You have a working mini web app.

---

## **3️⃣ Learn Docker basics + create a Dockerfile (1 hour)**

You learn:

- What a container is
    
- How Docker builds an image
    
- How to run a container locally
    

Tasks:

- Write a simple Dockerfile
    
- Run: `docker build`
    
- Run: `docker run`
    

Outcome:  
Your app now runs **inside Docker**.

---

## **4️⃣ Set up your cloud environment (2 hours)**

Based on your cloud (GCP recommended):

You do:

- Create project
    
- Enable Cloud Run and Artifact Registry
    
- Create Artifact Registry repo
    
- Create service account
    
- Create JSON key
    
- Add key to GitHub Secrets
    

Outcome:  
Your cloud is ready to receive images.

---

# ✔️ End of Day 1 Result

By the end of Day 1:

- You understand the pipeline
    
- You have a working app
    
- You have a working Docker image
    
- Cloud is ready
    
- GitHub secrets are ready
    

Perfect foundation for Day 2.

---

# 🗓️ **DAY 2 — Build the CI/CD Pipeline + Deploy**

Goal:  
✔ Write the GitHub Actions pipeline  
✔ Build and push Docker image automatically  
✔ Run code scan  
✔ Deploy to Cloud Run  
✔ Verify live service

---

## **1️⃣ Create GitHub Actions workflow (2 hours)**

You make `.github/workflows/cicd.yml` with these stages:

### ✓ Build

- checkout code
    
- authenticate to cloud
    
- build Docker image
    
- push to Artifact Registry
    

### ✓ Scan

- basic code scan (CodeQL or Trivy)
    

### ✓ Deploy

- deploy image to Cloud Run
    

Outcome:  
Your repo has a full CI/CD YAML file.

---

## **2️⃣ Run the pipeline (1 hour)**

You do:

- Push code to GitHub
    
- Watch Actions pipeline run:
    
    1. Build
        
    2. Scan
        
    3. Deploy
        

Outcome:  
Your image appears in Artifact Registry.

---

## **3️⃣ Verify the deployment (30 min)**

You check Cloud Run:

- A new revision is created
    
- A public URL is generated
    
- Open the URL → see “Hello World”
    

Outcome:  
Your CI/CD pipeline is **working end-to-end**.

---

## **4️⃣ (Optional) Understand logs + failures (30 min)**

You learn:

- How to view GitHub Action logs
    
- How to debug failed steps
    
- Why code scanning matters
    

Outcome:  
You understand how real pipelines are maintained.

---

# ✔️ End of Day 2 Result

By the end of Day 2:

- You have a full CI/CD pipeline from GitHub → Cloud
    
- Every push automatically builds, scans, and deploys
    
- You understand every stage practically
    
- You have a **complete DevOps pipeline project** you can show in portfolio
    

---

# 🎉 Final Outcome (after 2 days)

You will know **exactly**:

✔ How Docker packaging works  
✔ How GitHub Actions works  
✔ How to push images to Artifact Registry  
✔ How to deploy to Cloud Run  
✔ How to automate everything end-to-end  
✔ How real companies do DevOps pipelines