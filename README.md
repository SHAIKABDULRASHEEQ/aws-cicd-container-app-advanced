# AWS-Jenkins-Docker-Cicd

Production-style CI/CD pipeline built on AWS using Jenkins, Docker, GitHub, and Linux servers to automate application build and deployment.

---

## Project Overview

This project demonstrates an end-to-end Continuous Integration and Continuous Deployment (CI/CD) workflow using Jenkins integrated with GitHub. Whenever application code is updated, Jenkins pulls the latest source code, builds a Docker image, and deploys the updated containerized application to an AWS EC2 application server.

This project was created to simulate a real-world DevOps deployment process using industry-standard tools.

---

## Architecture

GitHub Repository  
↓  
Jenkins CI Server (AWS EC2)  
↓  
Docker Image Build  
↓  
Secure Copy to Application Server  
↓  
Container Deployment on AWS EC2  
↓  
Running Web Application

---

## Tech Stack

- AWS EC2
- Jenkins
- Docker
- GitHub
- Linux
- Shell Scripting
- CI/CD Pipelines

---

## Key Features

- Automated code checkout from GitHub
- Jenkins pipeline execution
- Docker image build automation
- Remote deployment to application server using SSH
- Automatic container restart with latest version
- Simplified release workflow
- Real-time deployment pipeline logs

---

## CI/CD Flow

1. Developer pushes latest code to GitHub repository  
2. Jenkins fetches updated source code  
3. Docker image is built automatically  
4. Docker image exported and transferred to application server  
5. Existing container stopped and removed  
6. New container started with latest image  
7. Updated application becomes available to users

---

## Important Files

- `Jenkinsfile` – Defines CI/CD pipeline stages  
- `Dockerfile` – Builds application image  
- `app/` – Application source code  
- `README.md` – Project documentation

---

## Sample Commands Used

- docker build -t devops-app .
- docker save devops-app -o devops-app.tar
- scp devops-app.tar ec2-user@server:/home/ec2-user/
- ssh ec2-user@server
- docker load -i devops-app.tar
- docker run -d -p 5000:5000 devops-app

---

## Results

- Automated deployment workflow
- Faster release cycle
- Repeatable container deployments
- Improved CI/CD understanding

---

## Key Learnings

- Jenkins pipeline stages
- Docker image lifecycle
- SSH deployment automation
- Linux troubleshooting

---

## Future Enhancements

- Push images to AWS ECR
- Add rollback stage
- Add testing stage
- Deploy to Kubernetes

---

## Author

Shaik Abdul Rasheeq  
Cloud / DevOps Engineer
