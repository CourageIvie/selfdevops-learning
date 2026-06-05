# MEMORY.md — Docker Learning

## Session: June 5, 2026

### What We Did
- Created first Docker container from scratch
- Built a Node.js web server app
- Packaged it into a Docker image
- Ran the container and verified it in the browser

### Project Location
`/c/Users/ejehi/Documents/DevOps-Learning/OMONYE-LEARNING/docker/my-first-container`

### Branch
`feature/my-first-docker-container`

### Files Created
- `app.js` — Node.js web server listening on port 3000
- `package.json` — Node app config with start script
- `Dockerfile` — Recipe to build the container image

### Image Built
- Name: `omonye-first-container`
- ID: `2a1fc4e7067b`
- Size: 1.58GB (large because node:20 base image is heavy)

### Container Run
- Name: `omonye-container`
- ID: `fba4cba4d3aa`
- Port mapping: `0.0.0.0:3000->3000/tcp`
- Result: Browser showed "Hello from Omonye first Docker container!"

### Git
- Committed and pushed to `feature/my-first-docker-container`
- PR link: https://github.com/CourageIvie/selfdevops-learning/pull/new/feature/my-first-docker-container

### Next Session
- Docker Compose — running multiple containers together
