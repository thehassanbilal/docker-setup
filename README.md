
---

# Dockerizing a NestJS Application

This guide will help you Dockerize your NestJS application, making it easier to set up and manage in different environments.

## Prerequisites

Before you start, make sure you have:

- Basic knowledge of Docker.
- A working NestJS application.
- Docker installed on your system. You can download it from [Docker's official website](https://docs.docker.com/get-docker/).

## Step 1: Create a Dockerfile

Create a `Dockerfile` in the root directory of your NestJS project with the following content:

```Dockerfile
# Step 1: Use the official Node.js runtime as a base image
FROM node:20.16.0

# Step 2: Set the working directory inside the container
WORKDIR /app

# Step 3: Copy package.json and package-lock.json files to the container
COPY package*.json ./

# Step 4: Install dependencies
RUN npm install

# Step 5: Copy the rest of the application code to the container
COPY . .

# Step 6: Build the NestJS application
RUN npm run build

# Step 7: Expose the port on which the app will run
EXPOSE 3000

# Step 8: Run the NestJS application
CMD ["npm", "run", "start:prod"]
```

## Step 2: Create a `.dockerignore` File

Create a `.dockerignore` file in the root directory with the following content:

```plaintext
# Node modules
node_modules

# Build files
dist

# Docker files
Dockerfile
docker-compose.yml
.dockerignore

# Git files
.git
.gitignore
```

## Step 3: Build the Docker Image

Build the Docker image for your NestJS application by running the following command in your project's root directory:

```bash
docker build -t your-app-name .
```

Replace `your-app-name` with a suitable name for your Docker image.

## Step 4: Run the Docker Container

Run the Docker container using the following command:

```bash
docker run -p 3000:3000 your-app-name
```

## Step 5: Optional - Use Docker Compose

If your application depends on multiple services (e.g., a database), you can manage them with Docker Compose. Create a `docker-compose.yml` file with the following content:

```yaml
version: '3.8'
services:
  app:
    image: your-app-name
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
      - MONGO_URI=mongodb://mongo:27017/your-database-name
      - PORT=3000
    depends_on:
      - mongo
    networks:
      - your-network-name
  mongo:
    image: mongo:latest
    ports:
      - "27017:27017"
    volumes:
      - mongo-data:/data/db
    networks:
      - your-network-name
volumes:
  mongo-data:
networks:
  your-network-name:
    driver: bridge
```

## Step 6: Run the Application with Docker Compose

Start all services defined in the `docker-compose.yml` file with the following command:

```bash
docker-compose up -d
```

## Step 7: Access Your Application

Once the containers are running, your NestJS application should be accessible at `http://localhost:3000`.

## Step 8: Stop the Containers

To stop and remove all containers, networks, and volumes defined in the `docker-compose.yml`, run:

```bash
docker-compose down
```

## Step 9: Debugging and Logs

To view the logs of a running container, use:

```bash
docker logs <container_id_or_name>
```
