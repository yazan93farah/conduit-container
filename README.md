# Conduit Container Project

This project is a containerized version of the Conduit application.
It consists of a Django-based backend providing the REST API.
The frontend is implemented with Angular and served via NGINX.
Both services run in separate Docker containers on same network.
Docker Compose is used to manage and deploy the complete application stack.

## Table of Contents
1. [Prerequisites](#Prerequisites)
2. [Quickstart](#Quickstart)
3. [Usage](#Usage)
   - [Stop Docker Container](#Stop-Docker-Container)
   - [Delete Docker Container](#Delete-Docker-Container)
4. [Logs](#Logs)

## Prerequisites
- Docker 
- Docker Compose 

## Quickstart
1. Clone the following Git Repository: 
```bash
git clone git@github.com:yazan93farah/conduit-container.git
```

2. Navigate to the Cloned Repo-Direcotry: 
```bash
cd conduit-container
```

3. Clone all Submodules 
```bash
git submodule update --init --recursive
```

4. Copy your Backend Environement file.
Naviagte: 
```bash
cd conduit-backend
```

Copy the File: 
```bash
cp example.env .env
```

Navigate Back to Root: 
```bash
cd ..
```

5. Copy your Frontend Environement file.
Naviagte: 
```bash
cd conduit-frontend
```

Copy the File: 
```bash
cp example.env .env
```

Navigate Back to Root: 
```bash
cd ..
```

6. Build Docker Compose 
```bash
docker compose build 
```

7. Start Docker Compose 
```bash
docker compose up -d 
```
-d  Detached mode: Run containers in the background


## Usage 
### start Docker Container 
To Stop the Container use the following Command: 
```bash
docker compose up -d 
```
-d  Detached mode: Run containers in the background


### Stop Docker Container 
To Stop the Container use the following Command: 
```bash
docker compose down 
```

## Logs 
### Show Logs Docker Container 
To show the Container logs use: 
```bash
docker logs [container-name] 
```
### Save logs in a File
To save logs in a file use:
```bash
docker logs [container-name] > <container-name>-logs.txt
```
