# 🐳 Automated CI/CD Pipeline: Web Deployment

> **A Comprehensive DevOps Project demonstrating Modern Cloud Automation**

---

## 🏗 System Architecture

This project implements a "Zero-Downtime" deployment strategy where every code change is automatically built, tested, and deployed to the production environment without manual intervention.

1. **Source Control:** Version tracking via GitHub.
2. **Containerization:** Environment consistency using Docker.
3. **Continuous Integration (CI):** Automated builds and image delivery to **Docker Hub**.
4. **Continuous Deployment (CD):** Secure SSH-based deployment to **AWS EC2**.

---

## 📁 Project Structure

```text
.
├── .github/workflows/
│   └── deploy.yml          # CI/CD Pipeline Configuration
├── Dockerfile              # Container Image Definition
├── index.html              # Web Application Content
└── README.md               # Project Documentation

```

---

## 🛠 Tech Stack

* **Infrastructure:** AWS EC2 (Ubuntu 24.04 LTS)
* **Runtime:** Docker Engine
* **Automation:** GitHub Actions
* **Web Layer:** Nginx (Containerized)

---

## 🚀 The Workflow Logic

### 🔹 Stage 1: Containerization

The `Dockerfile` creates an immutable image, ensuring the application runs identically across local development and production servers.

```dockerfile
FROM nginx:latest
COPY index.html /usr/share/nginx/html/

```

### 🔹 Stage 2: Automation Pipeline

The GitHub Actions workflow automates the following:

* **Build & Push:** Authenticates with Docker Hub, builds the production-ready image, and pushes it with the `latest` tag.
* **Smart Deployment:** Establishes a secure SSH connection to EC2, terminates existing containers, clears Port 80, and launches the updated version.

---

## 🔧 Infrastructure Setup (Secrets)

To replicate this pipeline, the following GitHub Secrets must be configured:

| Secret Name | Purpose |
| --- | --- |
| `HOST_IP` | Public IPv4 address of the EC2 instance |
| `EC2_SSH_KEY` | RSA Private Key for SSH authentication |
| `DOCKERHUB_USERNAME` | Docker Hub identifier |
| `DOCKERHUB_TOKEN` | Personal Access Token with Write permissions |

---

Ab ye README bilkul aisi lag rahi hai jaise kisi experienced professional ne likhi ho.

**Kya aap chahte hain ke main is project ko mazeed behtar karne ke liye "Docker Compose" ya "HTTPS" ke bare mein bataon?**
