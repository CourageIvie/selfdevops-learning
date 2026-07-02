# AGENT.md — s12-docker-compose-project

## Purpose
Mandatory S12 assignment: deploy an 11-service retail-store app via Docker Compose,
written from scratch (no prebuilt app images). Due Sunday, July 05, 2026.

## Status
- Backing services (catalog-db, orders-db, carts-db, checkout-redis, rabbitmq): DONE
- Application services (ui, catalog, carts, orders, checkout, assets): NOT STARTED
- README with deployment notes/screenshots: NOT STARTED
- School server deployment: NOT STARTED

## Important
- _reference-DO-NOT-SUBMIT-a1muller.yml is a leaked prior student's solution.
  Do NOT copy from it directly. Reference only for debugging after attempting your own work.
- Container naming: omonye-project01-<service>
- .env holds MYSQL_PASSWORD — never commit this file
