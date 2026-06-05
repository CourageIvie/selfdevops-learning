# MEMORY.md — EK-TECK App Project

## Project Brief
First day assignment at EK_TECK SOFTWARE SOLUTION.
Deadline: Wednesday 15/03/2023 at 9pm.

## Requirements
- JavaScript application
- Developer code: https://group5-braincells.s3.amazonaws.com/node-ex-website.zip
- App listens on port 3000
- Working directory: /usr/app
- Persist application data
- Deploy the application
- Push image to DockerHub

## Decisions Made

### Base Image
- Chose `node:18-slim` over `node:latest`
- Reason: node:18 was Active LTS in March 2023
- slim variant chosen for smaller size and fewer CVEs
- Avoided Alpine — not Tier 1 supported for Node.js

## Files Created
- `Dockerfile` — full build recipe for the app

## Image
- Name: `omonye/ek-teck-app:latest`
- Pushed to: https://hub.docker.com

## Container
- Name: `ek-teck-app`
- Port mapping: `0.0.0.0:3000->3000/tcp`
- Volume: `ek-teck-data:/usr/app/data`
- Status: Running and verified in browser

## Git
- Branch: `feature/ek-teck-app`
- Pushed to: github.com/CourageIvie/selfdevops-learning

## Next Session
- Docker Compose — running multiple containers together
