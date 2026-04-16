# Chicken-Disease-Classification


## Workflow

1. Update Config.yaml
2. Update Secrets.yaml(optional)
3. Update params.yaml
4. Update the entity
5. Update the configuration manager in src config
6. Update the components
7. Update the pipeline
8. Update the main.py
9. Update the dvc.yaml

# Chicken Disease Classification Project

![App Interface](https://raw.githubusercontent.com/AssadKhurshid/Chicken-Disease-Classification-/refs/heads/main/interface.png)

## How to run?

### STEPS:

**Clone the repository**
```bash
git clone [https://github.com/entbappy/Chicken-Disease-Classification--Project](https://github.com/entbappy/Chicken-Disease-Classification--Project)

```markdown
# Chicken Disease Classification Project 🐣

![App Interface](https://raw.githubusercontent.com/AssadKhurshid/Chicken-Disease-Classification-/refs/heads/main/interface.png)

## Overview
This project is a Deep Learning based classification system that detects diseases in chickens (like Coccidiosis) using fecal images. It uses a CNN (Convolutional Neural Network) model and is deployed using a professional CI/CD pipeline on AWS.

---

## 🛠 How to run?

### 1. Clone the repository
```bash
git clone [https://github.com/AssadKhurshid/Chicken-Disease-Classification-](https://github.com/AssadKhurshid/Chicken-Disease-Classification-)
```

### 2. Create a Conda Environment
Open the repository folder and run:
```bash
conda create -n cnncls python=3.8 -y
conda activate cnncls
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Run the Application
```bash
python app.py
```
After running, open your browser and go to `localhost:8080` (or the port shown in your terminal).

---

## 📊 DVC (Data Version Control)
This project uses DVC to manage data pipelines and reproducibility:
```bash
dvc init
dvc repro
dvc dag
```

---

## 🚀 AWS CI/CD Deployment with GitHub Actions

### 1. IAM User Setup
Create an IAM user in AWS with the following policies:
1. `AmazonEC2ContainerRegistryFullAccess`
2. `AmazonEC2FullAccess`

### 2. ECR Repository
Create an Elastic Container Registry (ECR) to store your Docker images.
- **ECR URI:** `639267898772.dkr.ecr.us-east-1.amazonaws.com/chicken`

### 3. EC2 Setup (Ubuntu)
Launch a `t2.micro` instance (Ubuntu) and install Docker:
```bash
sudo apt-get update -y
curl -fsSL [https://get.docker.com](https://get.docker.com) -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker
```

### 4. Self-Hosted Runner
Go to `Settings > Actions > Runners` in your GitHub repo and follow the instructions to connect your EC2 instance as a runner.

### 5. GitHub Secrets
Add the following secrets in your repository settings (`Settings > Secrets and variables > Actions`):
| Secret Name | Description |
| :--- | :--- |
| `AWS_ACCESS_KEY_ID` | Your IAM User Access Key |
| `AWS_SECRET_ACCESS_KEY` | Your IAM User Secret Key |
| `AWS_REGION` | `us-east-1` |
| `AWS_ECR_LOGIN_URI` | `639267898772.dkr.ecr.us-east-1.amazonaws.com` |
| `ECR_REPOSITORY_NAME` | `chicken` |

---

## 🛠 Deployment Steps (Automated)
1. **Build:** GitHub Actions builds the Docker image.
2. **Push:** The image is pushed to AWS ECR.
3. **Deploy:** The Self-hosted runner on EC2 pulls the latest image and runs it as a container.
```


