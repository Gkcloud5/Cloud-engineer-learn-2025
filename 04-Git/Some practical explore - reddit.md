
### 🧩 1. **Set up your cloud environment**
- Create project, enable required services (Artifact Registry, Cloud Run, etc.).
- Create service account and credentials.
---
### 💻 2. **Create a sample app and Dockerfile**
- Write a simple “Hello World” app.
- Add a Dockerfile to package it.
---
### ☁️ 3. **Create an Artifact Registry (or Docker registry)**
- This will store your built Docker images.

---
### ⚙️ 4. **Set up GitHub Secrets**
- Store your cloud credentials and project details securely in GitHub.

---
### 🤖 5. **Create a GitHub Actions workflow**
- Automate:
    - **Build** → build Docker image    
    - **Scan** → run code checks    
    - **Deploy** → push to registry and deploy to Cloud Run
        
---
### ✅ 6. **Trigger and verify the pipeline**
- Push code to `main` → Actions run automatically.
- Check in GCP: image uploaded and app deployed successfully.

---
### 🌐 7. **Access your deployed app**
- Open the Cloud Run URL → see your “Hello World” live.

