# 🐳 Automated CI/CD Web Deployment with Docker & AWS


## 🏗 Project Architecture

1. **Code:** Simple `index.html` file.
2. **Containerization:** `Dockerfile` packages the website using an Nginx image.
3. **Automation (CI):** GitHub Actions builds the Docker image and pushes it to **Docker Hub** on every push.
4. **Deployment (CD):** GitHub Actions connects to **AWS EC2** via SSH, pulls the latest image, and runs it as a container.

---

## 🛠 Tech Stack

* **Cloud:** AWS (EC2)
* **Containerization:** Docker
* **Registry:** Docker Hub
* **CI/CD:** GitHub Actions
* **Web Server:** Nginx

---

## 🚀 How It Works

### 1. The Docker Magic

Every time I push code, a new image is created. This ensures that the environment is exactly the same on my computer and the server.

> **Dockerfile:** Uses `nginx:latest` and copies the local `index.html` to `/usr/share/nginx/html/`.

### 2. GitHub Actions Workflow

The workflow is divided into two main jobs:

* **Build & Push:** Logs into Docker Hub and uploads the new image.
* **Deploy:** Logs into EC2, stops the old container, clears Port 80, and runs the new version.

---

## 🔧 Setup & Configuration

To replicate this project, you need to set up the following **GitHub Secrets**:
| Secret Name | Description |
| :--- | :--- |
| `HOST_IP` | Public IP of the EC2 Instance |
| `EC2_SSH_KEY` | Private `.pem` key for AWS |
| `DOCKERHUB_USERNAME` | Your Docker Hub ID |
| `DOCKERHUB_TOKEN` | Docker Hub Access Token (Read/Write) |

---

## 🎯 Key Learnings

* How to handle **Port Conflicts** (killing processes on Port 80).
* Managing **Docker Permissions** for the `ubuntu` user.
* Automating **SSH** commands via GitHub Actions.
* Security best practices using GitHub Secrets.

---
