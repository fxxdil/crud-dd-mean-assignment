
# MEAN CRUD Application — DevOps Assignment

A full-stack **MEAN** CRUD application fully containerized using Docker and deployed on **AWS EC2** with **Docker Compose**, **Nginx reverse proxy**, and a fully automated **GitHub Actions CI/CD pipeline**.

##  Features
- Backend: Node.js + Express (Dockerized)
- Frontend: Angular + Nginx (Dockerized)
- Database: MongoDB (Docker container)
- Deployment: AWS EC2 (Ubuntu 22.04 LTS)
- CI/CD: GitHub Actions → Docker Hub → AWS EC2 auto-deploy

## Repository Structure
```
.
├── backend/
│   ├── Dockerfile
│   ├── server.js
│   ├── app/
│   └── package.json
│
├── frontend/
│   ├── Dockerfile
│   ├── nginx.conf
│   ├── src/
│   └── package.json
│
├── docker-compose.yml
│
└── .github/
    └── workflows/
        └── cicd.yml
```

##  Docker Compose Deployment
Run this in AWS EC2:
```
docker compose pull
docker compose up -d
```

App will be live at:
```
http://13.126.38.104/
```

# CI/CD Pipeline Steps
1. Push to **main** branch  
2. GitHub Actions builds Docker images  
3. Images pushed to Docker Hub  
4. GitHub Actions SSHes into AWS  
5. AWS pulls latest images  
6. Containers restart automatically  

# GitHub Secrets Required
| Secret | Description |
|--------|-------------|
| DOCKERHUB_USERNAME | Your Docker Hub username |
| DOCKERHUB_TOKEN | Docker Hub Access Token |
| VM_HOST | EC2 Public IP |
| VM_USER | ubuntu |
| VM_SSH_KEY | Private key (.pem) content |

## 📸 Screenshots to Include 
- GitHub Actions successful run  

- Docker Hub pushed images
![alt text](image-7.png)
- EC2 instance running  
![alt text](image-8.png)
- `docker ps` output  
![alt text](image-9.png)
- Application UI in browser  
![alt text](image-10.png)
- docker-compose.yml  
![alt text](image-11.png)
- Repository structure screenshot
![alt text](image-12.png)  


## 📌 Notes
- Do not delete the EC2 instance  
- Stopping the instance is allowed  
