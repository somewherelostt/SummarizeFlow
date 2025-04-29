# SummarizeFlow
---

# 📝 End-to-End Text Summarizer Project

This project is a complete end-to-end implementation of a text summarization system, built using Python and deployable using Docker and AWS CI/CD with GitHub Actions.

---

## 📌 Project Workflow

1. Update `config.yaml`
2. Update `params.yaml`
3. Update entities
4. Update the Configuration Manager in `src/config`
5. Update components
6. Update the pipeline
7. Update `main.py`
8. Update `app.py`

---

## 🚀 How to Run

### 🧱 Clone the Repository

```bash
git clone https://github.com/somewherelostt/SummarizeFlow.git
cd End-to-end-Text-Summarization
```

### 🐍 Step 1: Create Conda Environment

```bash
conda create -n summary python=3.8 -y
conda activate summary
```

### 📦 Step 2: Install Requirements

```bash
pip install -r requirements.txt
```

### ▶️ Step 3: Run the Application

```bash
python app.py
```

Open your browser and navigate to your local host and port (typically `http://127.0.0.1:5000`).

---

## ☁️ AWS CI/CD Deployment with GitHub Actions

### Step-by-step Deployment Process

#### 1. Login to AWS Console

Create an IAM user with the following permissions:

- **AmazonEC2ContainerRegistryFullAccess**
- **AmazonEC2FullAccess**

#### 2. Setup AWS Services

- **ECR (Elastic Container Registry):** Create a repository to store Docker images  
  Example URI:  

  ```
  566373416292.dkr.ecr.us-east-1.amazonaws.com/text-s
  ```

- **EC2 (Elastic Compute Cloud):** Launch a new Ubuntu instance

#### 3. Install Docker on EC2

```bash
sudo apt-get update -y
sudo apt-get upgrade
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker
```

#### 4. Configure EC2 as a Self-hosted GitHub Runner

- Go to your GitHub repo:
  - Settings → Actions → Runners → New self-hosted runner
  - Choose OS: Linux
  - Follow setup commands shown

#### 5. Set GitHub Secrets

In your repository:

- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_REGION` (e.g., `us-east-1`)
- `AWS_ECR_LOGIN_URI` (e.g., `566373416292.dkr.ecr.us-east-1.amazonaws.com`)
- `ECR_REPOSITORY_NAME` (e.g., `text-s`)

---

## 📦 Docker Deployment Overview

1. Build Docker image of the app
2. Push image to ECR
3. Pull image in EC2 instance
4. Run the container on EC2

---

Let me know if you'd like me to generate the actual `README.md` file or include a GitHub Actions workflow example (`.github/workflows/deploy.yml`).
