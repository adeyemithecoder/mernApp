# ===============================

# DOCKER VERSION / TEST

# ===============================

# Check docker version

docker --version

# Test docker installation

docker run hello-world

# ===============================

# BUILD IMAGES

# ===============================

# Build MERN backend image

docker build -t mern-backend .
docker run -p 5000:5000 --name backend --env-file .env mern-backend

# Build backend with version tag

docker build -t mern-backend:1.0 .

# Build frontend image (pass API URL)

docker build -t mern-frontend --build-arg VITE_API_URL=http://localhost:5000/api .

# ===============================

# RUN CONTAINERS

# ===============================

# Run backend container

docker run -d -p 5000:5000 --name backend --env-file .env mern-backend

# Run frontend container

docker run -d -p 5173:5173 --name frontend mern-frontend

# ===============================

# CONTAINER MANAGEMENT

# ===============================

# Show running containers

docker ps

# Show all containers

docker ps -a

# Stop container

docker stop <container-id>

# Stop multiple containers

docker stop container1 container2 container3

# Start container

docker start <container-id>

# Restart container

docker restart <container-id>

# Remove container

docker rm <container-id>

# Force remove container

docker rm -f <container-id>

# Remove all stopped containers

docker container prune

# ===============================

# IMAGE MANAGEMENT

# ===============================

# Show images

docker images

# Remove image

docker rmi <image-name>

# Remove multiple images

docker rmi image1 image2 image3

# Force remove image

docker rmi -f <image-name>

# ===============================

# LOGS

# ===============================

# Backend logs

docker logs backend

# Frontend logs

docker logs frontend

# Live logs

docker logs -f backend

# ===============================

# EXECUTE COMMAND INSIDE CONTAINER

# ===============================

docker exec -it backend sh

# ===============================

# QUICK CLEANUP

# ===============================

# Stop containers

docker stop backend frontend

# Remove containers

docker rm backend frontend

# Remove unused images

docker image prune

# Clean entire docker system

docker system prune -a

# ===============================

# DOCKER COMPOSE COMMANDS

# ===============================

# Build and start services

docker compose up --build

# Start services in background

docker compose up -d

# Stop services

docker compose down

# Restart services

docker compose restart

# View running compose containers

docker compose ps

# View logs

docker compose logs

docker compose logs backend

# Live logs

docker compose logs -f

# Stop and remove containers, networks

docker compose down --volumes

# CLIENT SETUP

# Install ESLint, Prettier, and React linting plugins for the client project

npm i -D eslint prettier @eslint/js globals eslint-plugin-react-hooks eslint-plugin-react-refresh

# SERVER SETUP

# Install ESLint and Prettier for the server project

npm i -D eslint prettier

{
"scripts": {
// Runs ESLint to check JavaScript and TypeScript files for issues
"lint": "eslint . --ext .js,.jsx,.ts,.tsx",

    // Runs ESLint and automatically fixes problems where possible
    "lint:fix": "eslint . --ext .js,.jsx,.ts,.tsx --fix",

    // Formats all files in the project using Prettier
    "format": "prettier --write ."

}
}

# Connect to a remote EC2 server using an SSH private key

ssh -i "C:\Users\sanga\.ssh\keypair3.pem" ec2-user@3.26.242.54
Explanation:
ssh -i "C:\Users\ADEYEMI\all_secret\mernApp.pem" ec2-user@16.171.65.85

ssh → starts an SSH connection.

-i "C:\Users\sanga\.ssh\keypair3.pem" → specifies the private key file used for authentication.

ec2-user → the username for the remote server (common default for Amazon Linux EC2 instances).

3.26.242.54 → the public IP address of the server you are connecting to.

AWS Deployment Commands

# Connect to your EC2 instance using SSH and a private key

ssh -i "<path>" ec2-user@IP

# Create or edit a shell script file

nano file_name.sh
nano install_docker_amazon.sh

# Make the script executable

chmod +x file_name.sh

# Run the script

./file_name.sh

Install Docker Compose

# Create directory for Docker CLI plugins

sudo mkdir -p /usr/local/lib/docker/cli-plugins

# Download Docker Compose binary

sudo curl -SL https://github.com/docker/compose/releases/download/v2.29.2/docker-compose-linux-x86_64 \
-o /usr/local/lib/docker/cli-plugins/docker-compose

# Make Docker Compose executable

sudo chmod +x /usr/local/lib/docker/cli-plugins/docker-compose

# Check Docker Compose version

docker compose version

# Install Git on the server

sudo dnf install -y git

PORT=5000
NODE_ENV=production
MONGODB_URI=ADD_URI_HERE

VITE_API_URL=http://EC2_IP:5000/api

server/.dockerignore
node_modules
npm-debug.log
Dockerfile
.dockerignore
.git
.gitignore
.env
coverage
dist

#!/bin/bash

echo "Updating system packages..."
sudo dnf update -y

echo "Installing Docker..."
sudo dnf install -y docker

echo "Adding ec2-user to docker group..."
sudo usermod -aG docker ec2-user

echo "Enabling and starting Docker service..."
sudo systemctl enable docker
sudo systemctl start docker

echo "Verifying Docker installation..."
docker --version || echo "Docker not found in current session (re-login may be required)."

echo
echo "Docker installation complete on Amazon Linux 2023!"
echo "IMPORTANT: Log out and log back in (or run 'newgrp docker')"
echo "so that 'ec2-user' can run docker without sudo."
echo
echo "After re-login, test with:"
echo "docker run hello-world"

chmod +x install_docker_amazon.sh
chmod +x install_docker_amazon.sh
