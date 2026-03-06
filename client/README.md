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
