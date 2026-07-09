# S13 - Future Tech Leaders Docker Deployment

## Assignment
Clone, containerize, and run a website using Docker Compose.
Source: https://github.com/derickdevops/Future-Tech-Leaders/tree/future/dev

## Branch
feature/future-tech-leaders-docker (branched from main)

## Key findings
- Repo already contained a working Dockerfile and docker-compose.yml
  (3-stage build: deps -> builder -> runner, using Next.js `output: standalone`)
- No new Dockerfile/compose needed - verified existing ones instead of writing from scratch
- Container name: future-tech-leaders-web
- Port mapping: host 3001 -> container 3000

## Security note
The repo's committed .env.local contained a real (leaked) Supabase
service-role key and admin password. Did NOT reuse it. Replaced with:
  cp .env.example .env.local
(placeholder values only - Supabase-backed features won't work until
real credentials are added, which is expected for this exercise).

## Steps completed
1. git clone -b future/dev <repo-url> s13-future-tech-leaders
2. Reviewed structure - confirmed Dockerfile + docker-compose.yml exist
3. Verified Dockerfile (no changes needed)
4. Verified docker-compose.yml (no changes needed)
5. docker compose build  -> Built successfully in ~169s
6. docker compose up -d  -> Container Up, port 0.0.0.0:3001->3000/tcp
7. Verified: curl -I http://localhost:3001 -> HTTP/1.1 200 OK
   Homepage confirmed rendering in browser (Future Tech Leaders content)
8. Practiced stop/restart: docker compose down / up -d, and
   docker compose restart

## Environment note
Working from WSL Ubuntu on the /mnt/c/... Windows-mounted path.
Build was noticeably slower here (npm ci ~79s, next build ~51s)
due to the WSL<->Windows filesystem bridge.
