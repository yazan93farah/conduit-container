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
5. [Environment Variables](#environment-variables)

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

4. Copy Backend Environement file.
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


5. Copy Frontend Environement file.
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
6. Copy the Database Environement File: 
```bash
cp example.database.env .database.env
```

7. Build Docker Compose 
```bash
docker compose build 
```

8. Start Docker Compose 
```bash
docker compose up -d 
```
-d  Detached mode: Run containers in the background


## Usage 
### start and Stop Docker Container 
To Stop the Container use the following Command: 
```bash
docker compose up -d 
```
-d  Detached mode: Run containers in the background

and To Stop the Container use the following Command: 
```bash
docker compose down 
```

### Accessing Django Admin Console

to Start the admin Console for Django use:
```text
http://<your-ip>:<django-port>/admin  # default port is 5000 
```
Authentication is performed using credentials provided via environment variables.
For security reasons, these credentials should be changed after the initial login.

### Angular App

to Start the Angular App use:
```text
http://<your-ip>:<angular-port>   # default port is 8282 
```
Users must first complete the sign-up process, then log in to begin posting articles. 

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
## Environment Variables 
This Environment variables can be modified in the example.env before being copied 

### Database
```env
POSTGRES_DB=conduit                   # Database Name
POSTGRES_USER=conduit_user            # Database username
POSTGRES_PASSWORD=conduit_password    # Database password 
POSTGRES_HOST=database                # Database host
POSTGRES_PORT=5432                    # Database port
```

### Backend  
```env
DJANGO_HOST_PORT=5000        # Change DJANGO application port 
WORKERS=2                        # Gunicorn worker count
DJANGO_SUPERUSER_EMAIL=testaccount@gmail.com   # Admin user email
DJANGO_SUPERUSER_USERNAME=testingaccount       # Admin username
DJANGO_SUPERUSER_PASSWORD=AccountPasswordStrong123 # Admin password
ALLOWED_HOSTS=localhost,127.0.0.1 # Allowed request hosts
CORS_ORIGIN_WHITELIST=0.0.0.0:8282,localhost:8282 # Allowed origins 
DJANGO_SECRET_KEY='your-Key'  # Django Secret Key (new Key must be generated)
```
### Frontend
```env
API_URL=http://localhost:5000/api # Backend API endpoint
ANGULAR_HOST_PORT=8282 # Change Angular application port 

```
