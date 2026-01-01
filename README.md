# Mlops - Production-Ready-Machine-Learning-Project

- Anaconda: https://www.anaconda.com/
- Vs code: https://code.visualstudio.com/download
- Git: https://git-scm.com/
- Flowchart: https://whimsical.com/
- MLOPs Tool: https://www.evidentlyai.com/
- MongoDB: https://account.mongodb.com/account/login
- Data link: https://www.kaggle.com/datasets/moro23/easyvisa-dataset

# AWS CI/CD Deployment with GitHub Actions

This repository implements an end-to-end CI/CD pipeline using GitHub Actions, Docker, AWS ECR, and EC2 to deploy a Python-based Machine Learning / Backend application.

## Project Structure

├── constants
├── entity
├── components
├── pipeline
├── main.py
├── requirements.txt
├── Dockerfile
└── README.md

## Git Commands

git add .
git commit -m "Updated"
git push origin main

## Environment Setup (Conda)

conda create -n visa python=3.8 -y
conda activate visa
pip install -r requirements.txt

## Environment Variables

export MONGODB_URL="mongodb+srv://<username>:<password>@cluster.mongodb.net/..."

export AWS_ACCESS_KEY_ID=<AWS_ACCESS_KEY_ID>
export AWS_SECRET_ACCESS_KEY=<AWS_SECRET_ACCESS_KEY>

## Application Workflow

constants – global configuration values

entity – data schemas and artifacts

components – core ML and processing logic

pipeline – training and inference pipelines

main.py – application entry point

# AWS CI/CD Deployment Using GitHub Actions
Step 1: Login to AWS Console

Create an IAM user with programmatic access for deployment.

Step 2: Attach IAM Policies

AmazonEC2ContainerRegistryFullAccess
AmazonEC2FullAccess

Step 3: Create ECR Repository

Create an Elastic Container Registry (ECR) repository to store Docker images.

Example ECR URI:
315865595366.dkr.ecr.us-east-1.amazonaws.com/visarepo

Save this URI for GitHub Secrets.

Step 4: Create EC2 Instance

Operating System: Ubuntu
Instance Type: t2.micro or higher

Step 5: Install Docker on EC2

sudo apt-get update -y
sudo apt-get upgrade -y

curl -fsSL https://get.docker.com
 -o get-docker.sh
sudo sh get-docker.sh

sudo usermod -aG docker ubuntu
newgrp docker

Step 6: Configure EC2 as Self-Hosted GitHub Runner

Go to your GitHub repository
Settings → Actions → Runners → New self-hosted runner
Choose Linux
Run the provided commands on the EC2 instance

Step 7: Configure GitHub Secrets

Go to: Repository → Settings → Secrets and variables → Actions

## Add the following secrets:

AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_DEFAULT_REGION
ECR_REPO

## CI/CD Workflow Description

Build Docker image from source code

Push Docker image to AWS ECR

GitHub Actions triggers deployment

EC2 pulls Docker image from ECR

Docker container runs on EC2

## Technologies Used

Python 3.8
Docker
GitHub Actions
AWS EC2
AWS ECR
MongoDB
Conda

## Author
Venkata Manideep Patibandla
