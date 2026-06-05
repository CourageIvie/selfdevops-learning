# SKILLS.md — EK-TECK App Skills

## Docker Commands Used

### Build image with DockerHub tag
```bash
docker build -t <dockerhub-username>/<image-name>:latest .
```

### Run container with volume
```bash
docker run -d -p <host-port>:<container-port> -v <volume-name>:<container-path> --name <container-name> <image>
```

### Remove a container
```bash
docker rm -f <container-name>
```

### Stop a container
```bash
docker stop <container-name>
```

### Login to DockerHub
```bash
docker login
```

### Push image to DockerHub
```bash
docker push <dockerhub-username>/<image-name>:latest
```

## Key Lessons

### Base Image Selection
- Always research the correct base image before writing a Dockerfile
- For Node.js production: use `node:<version>-slim` not `node:latest`
- Pin versions e.g. `node:18-slim` not `node:latest`
- Avoid Alpine for Node.js — not Tier 1 supported

### Image Naming for DockerHub
- Must follow format: `username/image-name:tag`
- Example: `omonye/ek-teck-app:latest`
- Wrong tag = push rejected by DockerHub

### Data Persistence
- Use named volumes: `-v volume-name:/path/in/container`
- Declare mount point in Dockerfile with VOLUME instruction
- Named volumes survive container restarts and deletions

### Cleanup in Dockerfile
- Always clean up after apt installs
- Reduces image size significantly
```bash
apt-get clean && rm -rf /var/lib/apt/lists/*
```

### Port Conflicts
- Only one container can use a host port at a time
- Stop or remove the conflicting container before reusing a port
