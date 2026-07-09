# Lessons from S13 exercise

- Always inspect a cloned repo BEFORE writing new Dockerfile/compose
  files - this repo already had working ones.
- Never trust a committed .env file in someone else's repo; copy
  from .env.example and supply your own values.
- `docker compose config --services` / `docker compose ps` are the
  right way to VERIFY state, not assuming a command "worked."
- WSL and Git Bash have completely separate git configs and SSH
  keys - a repo touched from both can show mass false "modified"
  files from line-ending (CRLF/LF) differences. Fixed globally with
  a .gitattributes file: `* text=auto eol=lf`, then
  `git add --renormalize .`
- `git stash` is the safe way to set aside unfinished work before
  switching branches, rather than committing something half-done.
