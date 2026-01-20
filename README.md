# 🚀 DevOps Final Assignment – CI/CD with Kubernetes

This project demonstrates a complete **DevSecOps CI/CD pipeline** for a **Node.js backend application**, deployed using **Docker** and **Kubernetes (Minikube)**.

---

## 📌 Tech Stack

- Backend: Node.js (Express)
- Database: MongoDB (environment-based)
- Containerization: Docker
- CI/CD: GitHub Actions
- Security Scanning: Trivy
- Orchestration: Kubernetes (Minikube)
- OS: Windows & Linux Compatible

---

## 🧱 Project Structure

```
Devops-Final-Assignment/
├── .github/
│   └── workflows/
│       └── ci.yml
├── k8s/
│   ├── deployment.yaml
│   └── service.yaml
├── src/
│   ├── config/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   └── app.js
├── server.js
├── Dockerfile
├── package.json
├── README.md
└── .dockerignore
```

---

## ⚙️ Application Overview

- RESTful Node.js API
- Health endpoint: `/health`
- MongoDB connection via environment variables
- Database Config: `src/config/db.js`
- Port: 4000 (Default)

---

## 🐳 Dockerization

### Build Image
```bash
docker build -t devops-node-api .
```

### Run Container

```bash
docker run -p 4000:4000 devops-node-api
```

---

## 🔁 CI Pipeline (GitHub Actions)

The CI pipeline runs on every push to the `main` branch.

### CI Stages

1. Code checkout
2. Node.js setup
3. Dependency installation
4. Lint checks (ESLint)
5. Unit tests (Jest)
6. Docker image build (Buildx)
7. Container health check
8. Security scan using Trivy
9. Push trusted image to DockerHub

### Security Policy

* CRITICAL vulnerabilities: ❌ fail pipeline
* HIGH vulnerabilities: ⚠️ reported but allowed

---

## 🔐 GitHub Secrets Used

| Secret Name        | Description             |
| ------------------ | ----------------------- |
| DOCKERHUB_USERNAME | Docker Hub username     |
| DOCKERHUB_TOKEN    | Docker Hub access token |

---

## ☸️ Kubernetes Deployment

Kubernetes deployment is managed using declarative manifests.

### Deployment

* 1 replica
* Image from DockerHub (`atharv123455/github-actions-devops-assignment-user1`)
* Container port: 4000

### Service

* Type: NodePort
* Exposed port: 40007
* Target port: 4000

---

## 🧪 Local Kubernetes Setup (Minikube)

No cloud subscription is required.

### Start Cluster

```bash
minikube start
```

### Deploy Application

```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

### Verify

```bash
kubectl get pods
kubectl get svc
```

### Access Application

```bash
minikube service devops-node-api-service-user1
```

---

## 🔄 CD Pipeline

The deployment to Kubernetes is currently handled via manual application of manifests, verifying the GitOps workflow.

* Triggered manually via `kubectl`
* Uses trusted Docker images from CI
* Verifies deployment rollout

---

## 🧠 Architecture Flow

```
Git Push
   ↓
CI Pipeline (Lint → Test → Scan → Build → Push)
   ↓
DockerHub (Trusted Image)
   ↓
Manual Deployment (kubectl apply)
   ↓
Kubernetes Deployment (Minikube)
```

---

## 🎯 Key DevOps Concepts Demonstrated

* CI/CD principle adherence
* Immutable Docker images
* DevSecOps (shift-left security with Trivy)
* Environment-based configuration
* Declarative Kubernetes deployment

---

## 📝 Notes for Evaluation

* Kubernetes is implemented using Minikube
* Local Kubernetes is sufficient for demonstration
* Application runs on port 4000

---

## ✅ Project Status

* CI Pipeline: Implemented and passing
* Docker Image: Built and published
* Kubernetes Deployment: Running
* Service Exposure: Verified

---

## 👤 Author

**Atharv Sanjay Jain**
DevOps Final Assignment
