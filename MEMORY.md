# MEMORY.md - Learning Journey & Decisions

## Profile
- **Name**: Ebiendele Omonye
- **Stage**: Complete DevOps beginner
- **Time Available**: < 1 hour/day (3-4 hours/week)
- **Location**: Port Harcourt, Nigeria
- **Goal**: Become job-ready in DevOps
- **Workspace**: /c/Users/ejehi/Documents/DevOps-Learning/OMONYE-LEARNING

## Phase 1 Progress - Day 1 (May 28, 2025)
### What I Did
- Set up AWS account
- Launched EC2 Ubuntu instance
- Connected via SSH: 34.207.197.95
- Learned basic Linux commands

### Commands Learned
- `pwd` - Print working directory
- `ls -la` - List files with details
- `touch` - Create empty file
- `echo` - Write text
- `cat` - Read file contents

### Key Lesson
**Precision matters in Linux** - Spaces in filenames are critical
- `myfile.txt` ≠ `my file.txt`
- Made mistake, fixed it, learned from it

### Hands-On Work
- Created file: myfile.txt
- Added content: "Hello Linux"
- Read file back successfully

## Current Focus
- Phase 1: Linux & Command Line Foundations
- AWS EC2 instance running
- Ready for next exercises

## Important Reminders
- Never delete files without approval
- Always explain what, why, how
- Stage, commit, push together
- Ask before making changes (unless approved)

## Next Session
- Continue Phase 1 exercises
- Learn more commands: grep, find, sed
- Start using GitHub for version control

## Session Summary - Day 1 Complete
### What I Accomplished
1. ✅ Built friend's Docker learning app (MAKING_BOXES)
2. ✅ Tested app - runs on http://localhost:3000
3. ✅ Set up AWS account
4. ✅ Launched EC2 Ubuntu instance
5. ✅ Connected via SSH: 34.207.197.95
6. ✅ Learned Phase 1 Linux commands (pwd, ls, touch, echo, cat)
7. ✅ Set up Git version control
8. ✅ Pushed code to GitHub

### Key Achievements
- Connected to real Linux server in AWS cloud
- Versioning work on GitHub professionally
- Made first Git commits and resolved merge conflicts
- Following DevOps best practices

### Time Spent
- ~2 hours total
- AWS setup: 30 min
- Linux learning: 30 min
- Git/GitHub: 40 min
- Documentation: 20 min

### Status
- AWS EC2 instance ready for Phase 1 continuation
- GitHub repository created and working
- Workspace organized for 7-phase learning

## Phase 1 Lesson 2 - File Permissions (Jun 1)
### Commands Learned
- chmod - Change file permissions
- Number codes: 644, 755, 777, etc.
- Understanding rwxr-xr-x format

### Exercises Done
- Created myfile.txt
- Changed permissions with chmod 644
- Understood permission groups: owner, group, others

### Key Takeaway
File permissions control who can read, write, execute files.
This is critical for security in DevOps.

### EC2 Instance
- New instance: 54.242.107.102
- Connected via SSH successfully

## Docker Networking Session - June 22, 2026
### What I Did
- Listed existing Docker networks with `docker network ls`
- Removed an old custom network `my-test-net`
- Created a fresh custom network `my-app-net`
- Launched 3 alpine containers on `my-app-net`
- Proved containers can ping each other by name (DNS works)
- Launched a container on default bridge network
- Proved default bridge network has NO DNS (ping by name fails)
- Cleaned up all containers and networks

### Key Lesson
Custom bridge networks have built-in DNS.
Containers on a custom network find each other by name.
Default bridge network has no DNS - containers can only reach each other by IP.
This is exactly what Docker Compose does automatically behind the scenes.

### Commands Learned
- `docker network ls` - List all networks
- `docker network create <name>` - Create custom network
- `docker network rm <name>` - Remove a network
- `docker network inspect <name>` - See network details
- `docker run -dit --name <name> --network <network> <image>` - Run container on specific network
- `docker exec -it <container> sh` - Get shell inside running container
- `ping -c 3 <container-name>` - Test connectivity by name
- `docker container prune` - Remove all stopped containers

### Branch
feature/docker-networking
feature/docker-networking
EOFcat >> MEMORY.md << 'EOF'

## Docker Network Connect Session - June 24, 2026
### What I Did
- Created two isolated networks: network-a and network-b
- Ran container-a on network-a and container-b on network-b
- Proved containers on different networks cannot talk (ping by name fails)
- Used docker network connect to add container-b to network-a while it was still running
- Proved container-a could now ping container-b by name (0% packet loss)
- Inspected container-b and confirmed it had two IP addresses (one per network)
- Cleaned up all containers and networks

### Key Lesson
docker network connect adds a running container to a second network without restarting it.
The container gets a new IP address on the new network.
This makes it reachable by name from containers on that network.
This is how you bridge two isolated networks in Docker.

### Commands Learned
- docker network connect [network] [container] - Connect running container to a network
- docker inspect [container] --format '{{json .NetworkSettings.Networks}}' - See all networks a container is on

### Branch
feature/docker-networking
