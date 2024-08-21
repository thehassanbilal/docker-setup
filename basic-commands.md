Some basic Docker commands to help you get started:

### 1. **Check Docker Version**
   - To check the installed version of Docker:
   ```bash
   docker --version
   ```

### 2. **List Docker Images**
   - To see all the Docker images on your system:
   ```bash
   docker images
   ```

### 3. **Pull an Image**
   - To download a Docker image from Docker Hub:
   ```bash
   docker pull <image_name>
   ```
   - Example:
   ```bash
   docker pull node:20.16.0
   ```

### 4. **Build an Image**
   - To build a Docker image from a `Dockerfile`:
   ```bash
   docker build -t <image_name> .
   ```
   - Example:
   ```bash
   docker build -t my-nestjs-app .
   ```

### 5. **Run a Container**
   - To create and run a container from an image:
   ```bash
   docker run -d -p <host_port>:<container_port> <image_name>
   ```
   - Example:
   ```bash
   docker run -d -p 3000:3000 my-nestjs-app
   ```

### 6. **List Running Containers**
   - To list all running Docker containers:
   ```bash
   docker ps
   ```

### 7. **Stop a Container**
   - To stop a running container:
   ```bash
   docker stop <container_id>
   ```

### 8. **Start a Stopped Container**
   - To start a stopped container:
   ```bash
   docker start <container_id>
   ```

### 9. **Remove a Container**
   - To remove a stopped container:
   ```bash
   docker rm <container_id>
   ```

### 10. **Remove an Image**
   - To remove a Docker image:
   ```bash
   docker rmi <image_name>
   ```

### 11. **View Container Logs**
   - To see the logs of a running container:
   ```bash
   docker logs <container_id_or_name>
   ```

### 12. **Execute a Command in a Running Container**
   - To run a command inside a running container (e.g., open a shell):
   ```bash
   docker exec -it <container_id_or_name> <command>
   ```
   - Example:
   ```bash
   docker exec -it my-nestjs-app /bin/bash
   ```

### 13. **Prune Unused Docker Objects**
   - To remove all stopped containers, unused networks, and dangling images:
   ```bash
   docker system prune
   ```

These commands cover the basics of working with Docker images and containers. They should help you manage your Docker environment efficiently.
