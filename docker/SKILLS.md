# SKILLS.md — Docker Skills

## Core Docker Commands

### Build an image
```bash
docker build -t <image-name> .
```

### Run a container
```bash
docker run -d -p <host-port>:<container-port> --name <container-name> <image-name>
```

### List running containers
```bash
docker ps
```

### List all images
```bash
docker images
```

## Dockerfile Instructions

| Instruction | Purpose |
|---|---|
| `FROM` | Base image to start from |
| `WORKDIR` | Set working directory inside container |
| `COPY . .` | Copy files into container |
| `RUN` | Execute a command during build |
| `EXPOSE` | Document the port the app listens on |
| `USER` | Set the user to run the app as |
| `CMD` | Command to start the app |
| `ENTRYPOINT` | Fixed command that always runs |

## Key Concepts
- Image = built package (like an installer)
- Container = running instance (like an installed app)
- Dockerfile = recipe that builds the image
- Port mapping = -p 3000:3000 bridges your machine to the container

## Best Practices
- Always pin base image versions e.g. node:20 not node:latest
- Always run as non-root user e.g. USER node
- Clean up after installs to keep image size small
- Install multiple packages in one RUN command to reduce layers
