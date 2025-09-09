# Docker Guide

This document provides a complete overview of how to work with Docker, from installation to advanced usage.

---

## 📦 1. Install Docker

### Linux (Ubuntu/Debian)
```bash
sudo apt update
sudo apt install -y ca-certificates curl gnupg lsb-release

# Add Docker’s official GPG key
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

# Set up repository
echo   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg]   https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" |   sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

### macOS
- Download [Docker Desktop](https://www.docker.com/products/docker-desktop/).
- Install and start Docker Desktop.

### Windows
- Install **Docker Desktop for Windows**.
- Enable **WSL2 Backend**.

### Linux Amazon EC2
```
sudo yum update -y
sudo amazon-linux-extras install docker -y
sudo service docker start
sudo usermod -a -G docker ec2-user

sudo systemctl enable docker (Auto Start on Boot)
```

Verify installation:
```bash
docker --version
docker compose version
```

---

## 🚀 2. Docker Basics

### Check Docker info
```bash
docker info
```

### Run your first container
```bash
docker run hello-world
```

### List running containers
```bash
docker ps
```

### List all containers (including stopped)
```bash
docker ps -a
```

### Stop / Start / Remove containers
```bash
docker stop <container_id>
docker start <container_id>
docker rm <container_id>
```
### Restart Container
```
docker restart <container_id>
```
---

## 📂 3. Images

### Search an image
```bash
docker search nginx
```

### Pull an image
```bash
docker pull nginx
```

### List images
```bash
docker images
```

### Remove an image
```bash
docker rmi <image_id>
```

---

## ⚙️ 4. Running Containers

### Run in background (detached mode)
```bash
docker run -d nginx
```

### Run with port mapping
```bash
docker run -d -p 8080:80 nginx
```

### Run with volume mounting
```bash
docker run -d -v $(pwd):/usr/share/nginx/html -p 8080:80 nginx
```

### Run with environment variables
```bash
docker run -d -e MYSQL_ROOT_PASSWORD=root mysql:8
```

---

## 🔗 5. Networking

### List networks
```bash
docker network ls
```

### Create a custom network
```bash
docker network create my_network
```

### Run containers in the same network
```bash
docker run -d --name db --network my_network mysql:8
docker run -d --name app --network my_network my_app_image
```

---

## 💾 6. Volumes

### Create a volume
```bash
docker volume create my_volume
```

### Use volume in container
```bash
docker run -d -v my_volume:/var/lib/mysql mysql:8
```

### List volumes
```bash
docker volume ls
```

### Remove volume
```bash
docker volume rm my_volume
```

---

## 📝 7. Dockerfile

A `Dockerfile` is used to build custom images.

**Example:**
```dockerfile
# Use official Node.js image
FROM node:18

# Create app directory
WORKDIR /usr/src/app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Copy source code
COPY . .

# Expose port
EXPOSE 3000

# Start application
CMD ["npm", "start"]
```

### Build and run
```bash
docker build -t my-node-app .
docker run -d -p 3000:3000 my-node-app
```

---

## 🔄 8. Docker Compose

Docker Compose is used to manage multi-container applications.

**docker-compose.yml Example:**
```yaml
version: "3.9"
services:
  db:
    image: mysql:8
    environment:
      MYSQL_ROOT_PASSWORD: root
    volumes:
      - db_data:/var/lib/mysql

  app:
    build: .
    ports:
      - "3000:3000"
    depends_on:
      - db

volumes:
  db_data:
```

### Commands
```bash
docker compose up -d
docker compose ps
docker compose logs -f
docker compose down
```

---

## 🧹 9. Clean Up

### Remove stopped containers
```bash
docker container prune
```

### Remove unused images
```bash
docker image prune
```

### Remove unused networks
```bash
docker network prune
```

### Remove everything unused
```bash
docker system prune -a
```

---

## 📚 10. Useful Resources

- [Docker Documentation](https://docs.docker.com/)
- [Docker Hub](https://hub.docker.com/)
- [Dockerfile Reference](https://docs.docker.com/engine/reference/builder/)
- [Compose File Reference](https://docs.docker.com/compose/compose-file/)

---

✅ With this guide, you can install Docker, work with images, containers, volumes, networks, build custom images, and manage multi-container apps with Docker Compose.
