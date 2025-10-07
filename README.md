# 🚀 Next.js DevOps Deployment - Assessment Project

This project demonstrates containerization, CI/CD automation, and Kubernetes deployment of a **Next.js** application using **Docker**, **GitHub Actions**, and **Minikube**.

---

## 🧩 Project Overview

**Objective:**  
Containerize and deploy a Next.js application using best DevOps practices.

**Tech Stack:**
- [Next.js](https://nextjs.org/)
- [Docker](https://www.docker.com/)
- [GitHub Actions](https://github.com/features/actions)
- [Kubernetes (Minikube)](https://minikube.sigs.k8s.io/)
- [GitHub Container Registry (GHCR)](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry)

---

## ⚙️ Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/avimehndi/internship-wexa.git
cd <repo-name>
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Run Locally (Development Mode)
```bash
npm run dev
```
Access the app at: http://localhost:3000


---

## Docker Setup

### 1. Build Docker Image
```bash
docker build -t nextjs-app .
```

### 2. Run Container
```bash
docker run -p 3000:3000 nextjs-app
```
Visit http://localhost:3000 to verify the containerized app.

---

## GitHub Actions (CI/CD)

A workflow (.github/workflows/build-and-push.yml) automates:

 - Building the Docker image
 - Tagging and pushing to GitHub Container Registry (GHCR)

Image Tag Convention: (Example)

```bash
 ghcr.io/avimehndi/nextjs-app:latest
```

---

## Kubernetes Deployment (Minikube)

### 1. Start Minikube
```bash
minikube start
```

### 2. Apply Kubernetes Manifests
```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

### 3. Check Deployment Status
```bash
kubectl get pods
kubectl get svc
```

### 4. Access the Application
Expose the service through Minikube:
```bash
minikube service nextjs-service
```

This will open your app in a browser with the Minikube IP and assigned port.

---

# Project Structure
```
├── .github/
│   └── workflows/
│       └── build-and-push.yml          # GitHub Actions CI/CD workflow
│
├── my-next-app/
│   ├── k8s/
│   │   ├── deployment.yaml           # Kubernetes deployment manifest
│   │   └── service.yaml              # Kubernetes service manifest
│   │
│   ├── .dockerignore                 # Files to exclude from Docker builds
│   ├── Dockerfile                    # Docker configuration for Next.js app
│   ├── package.json
│   ├── next.config.js
│   ├── pages/
│   ├── public/
│   ├── node_modules/
│   └── ... (other app files)
│
└── README.md
```

---

## Key Learnings

- Built and containerized a Next.js app with Docker
- Automated image build & push via GitHub Actions
- Deployed to Kubernetes using Minikube
- Practiced DevOps CI/CD fundamentals end-to-end
