# hello-jenkins — CI/CD Pipeline with Jenkins, Docker & AWS EC2

## Project Overview
A fully automated CI/CD pipeline built on AWS EC2 
using Jenkins, Docker and GitHub. Every code push 
automatically triggers the pipeline — building a 
Docker image, running tests, deploying the 
application and cleaning up. Zero manual steps.

## Architecture
- Developer pushes code to GitHub
- GitHub webhook triggers Jenkins automatically
- Jenkins pulls latest code from GitHub
- Docker image built from Dockerfile
- Tests run inside the container
- Application deployed
- Image cleaned up after build
- Build result — SUCCESS or FAILURE

## Tech Stack
| Tool | Purpose |
|------|---------|
| Jenkins | CI/CD automation server |
| Docker | Containerization |
| AWS EC2 | Jenkins host server |
| GitHub | Source code + webhook trigger |
| Linux/Bash | Server environment |

## Jenkins Pipeline Stages
```groovy
pipeline {
    agent any
    stages {
        stage('Checkout')          // pulls code from GitHub
        stage('Build Docker Image') // builds Docker image
        stage('Run Container')      // runs and tests app
    }
    post {
        always { // cleanup after every build }
    }
}
```

## Infrastructure Setup
- AWS EC2 — Ubuntu 24.04 LTS, t2.micro
- Security Groups — Port 22 (SSH), Port 8080 (Jenkins)
- IAM — least privilege access following AWS best practices
- GitHub webhook — auto triggers on every push to main

## Key Learning
- Pipeline as Code — entire CI/CD config in Jenkinsfile
- Docker containerization and image lifecycle management
- GitHub webhook integration for automated builds
- AWS EC2 setup and security configuration
- Jenkins installation and plugin configuration on Linux
