# Autoscaling Web Application on AWS EKS

A production-grade DevOps project demonstrating cloud-native 
infrastructure automation and CI/CD pipelines.

## Architecture
- **AWS EKS** — Managed Kubernetes cluster with 2 worker nodes
- **Terraform** — Infrastructure as Code for VPC, EKS, EC2, ALB
- **Docker** — Containerized Flask web application
- **GitHub Actions** — Automated CI/CD pipeline
- **HPA** — Horizontal Pod Autoscaler (scales 2-10 pods)

## Tech Stack
|      Tool      |        Purpose         |
|----------------|------------------------|
| AWS EKS        | Managed Kubernetes     |
| Terraform      | Infrastructure as Code |
| Docker         | Containerization       |
| GitHub Actions | CI/CD Pipeline         |
| kubectl        | Kubernetes CLI         |
| AWS ECR        | Container Registry     |
| AWS ALB        | Load Balancer          |

## Project Structure
eks-devops-project/
├── app/
│   ├── app.py          # Flask application
│   ├── Dockerfile      # Container definition
│   └── requirements.txt
├── kubernetes/
│   ├── deployment.yaml # K8s deployment
│   ├── service.yaml    # Load balancer service
│   └── hpa.yaml        # Autoscaler config
├── terraform/
│   ├── main.tf         # VPC + EKS infrastructure
│   ├── variables.tf    # Input variables
│   └── outputs.tf      # Output values
└── .github/
└── workflows/
└── deploy.yml  # CI/CD pipeline

## How It Works
1. Developer pushes code to GitHub
2. GitHub Actions automatically triggers
3. Docker builds and pushes image to AWS ECR
4. kubectl deploys new version to EKS
5. HPA scales pods based on CPU/memory load

## CI/CD Pipeline
![GitHub Actions](https://github.com/gokul-s05/eks-devops-project/actions/workflows/deploy.yml/badge.svg)

## Setup Instructions
```bash
# Clone the repo
git clone https://github.com/gokul-s05/eks-devops-project.git

# Initialize Terraform
cd terraform
terraform init
terraform apply

# Deploy to Kubernetes
kubectl apply -f kubernetes/
```
