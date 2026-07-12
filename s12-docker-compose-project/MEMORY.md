
## Session Update — S12 Docker Compose Project
- Fixed docker-compose.yml YAML corruption: lines 1-87 contained a leftover incomplete duplicate service block plus a stray `cat > docker-compose.yml << 'EOF'` line that had been pasted into the file by accident instead of the terminal. Deleted with `sed -i '1,87d' docker-compose.yml`. Backup saved as docker-compose.yml.bak.
- Fixed catalog service: DB_MIGRATE changed from "false" to "true" via `sed -i 's/DB_MIGRATE: "false"/DB_MIGRATE: "true"/' docker-compose.yml`.
- Current state: 10 of 11 services defined (ui service still missing). docker compose config runs clean with no errors.
- Still outstanding: add ui service, check DSN format issue with splunksqlx tracing wrapper, remove prior student's section from README.md.

## Session Update — July 12, 2026 — Restored Missing Services
- Found docker-compose.yml had regressed to only 5 services (catalog-db, orders-db, carts-db, checkout-redis, rabbitmq) - all 6 app services (ui, catalog, carts, orders, checkout, assets) were missing.
- Root cause unclear - likely an accidental overwrite during a prior debugging session.
- Compared docker-compose.yml.bak, .bak2, .bak3, .save by grepping service names. docker-compose.yml.bak3 was the only backup with all 11 services correctly defined, no duplicates.
- Restored docker-compose.yml from .bak3. Original broken file saved as docker-compose.yml.broken-5services.
- Validated with docker compose config - all 11 services confirmed, MYSQL_PASSWORD resolves correctly from .env.
- Ran docker compose up --build -d - full build took about 21 minutes, all 11 containers started or healthy.
- App confirmed accessible at http://localhost:8080 (ui service, only published port).
- Added debug backup files to .gitignore to keep them off the remote.
- Still outstanding: splunksqlx DSN format issue (not present in any current backup, may live in src/ Dockerfile or config, needs investigation). README.md still has prior student's section to remove.
