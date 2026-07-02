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

## S12 Docker Compose Project - Started (July 2, 2026)
### What I Did
- Cloned real assignment repo from github.com/DEL-ORG/s12-docker-compose-project
- Discovered leaked prior-student solution in docker-compose.yml, renamed it to _reference-DO-NOT-SUBMIT-a1muller.yml (not used)
- Created feature/omonye-docker-compose-project branch off main
- Wrote docker-compose.yml from scratch for the 5 backing services: catalog-db, orders-db, carts-db, checkout-redis, rabbitmq
- All 5 services started successfully via docker compose up -d

### Key Lesson
Build multi-service Compose files bottom-up: backing services (databases, brokers) first,
since they have no build dependencies. Healthchecks on catalog-db, orders-db, and rabbitmq
let dependent app services wait for "truly ready" not just "container started."

### Branch
feature/omonye-docker-compose-project

### Status
Backing services layer complete. Next: build the 6 application services (ui, catalog, carts, orders, checkout, assets) from source.
