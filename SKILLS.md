# SKILLS.md - Commands, Conventions & Lessons Learned

## Docker Networking

### Key Concepts
- Default bridge network: no DNS, containers cannot find each other by name
- Custom bridge network: has DNS, containers find each other by name
- Docker Compose automatically creates a custom network for all services
- Always create a custom network for multi-container apps

### Commands
| Command | Purpose |
|---------|---------|
| `docker network ls` | List all networks |
| `docker network create <name>` | Create a custom network |
| `docker network rm <name>` | Remove a network |
| `docker network inspect <name>` | Inspect network details |
| `docker run -dit --name <n> --network <net> <image>` | Run container on network |
| `docker exec -it <container> sh` | Open shell inside container |
| `docker container prune` | Remove all stopped containers |

### Rules
- Always name containers clearly (container1, web, db etc.)
- Always use --network flag when running containers for multi-container setups
- Remove containers before removing their network
- Verify every command with ls or inspect - never assume

## Git Workflow
- Always create a feature branch before working
- Branch naming: feature/<description>
- Never work directly on main
- Always stage, commit, push together

## Docker General
- Always verify commands worked - never assume
- Use docker ps to confirm containers are running
- Use docker ps -a to see stopped containers too
- Use -d flag to run containers in background

## Docker Network Connect
- docker network connect [network] [container] — add running container to a network
- docker inspect [container] --format '{{json .NetworkSettings.Networks}}' — see all networks container belongs to
- A container can belong to multiple networks simultaneously
- Each network gives the container a separate IP address
- You cannot connect two networks directly — you connect a container to both networks instead
- This is called network bridging — the container has one foot in each network
- Use this when a container needs to talk to containers on a different network

## Port Publishing (-p flag)
- Syntax: docker run -p [host-port]:[container-port] [image]
- Host port is always LEFT, container port is always RIGHT
- Host ports must be unique across all containers
- Container ports can repeat across containers
- 0.0.0.0:8080->80/tcp means host port 8080 forwards to container port 80
- Two containers sharing the same host port throws: port is already allocated
- Without -p: container is isolated from outside (on Linux/production)
- With -p: Docker opens a door from your machine into the container

## Docker Network Drivers
- bridge: default driver, containers get own IP, DNS works on custom bridge networks
- host: container shares machine network directly, no port mapping needed, no isolation
- none: zero network access, only loopback (127.0.0.1), no eth0 interface
- overlay: multi-host networking for Docker Swarm and Kubernetes (advanced)
- Always use bridge for local dev and production multi-container apps
- Use none when container needs zero network access for security
- Use host only when maximum network performance is needed and isolation is not required
