# Manager Library Infrastructure

Local development infrastructure for the Manager Library assessment. This repository owns the container setup, network, persistent volumes, and an initially empty PostgreSQL database.

## Target stack

- Docker Compose
- PostgreSQL 16
- Laravel API and React app from their sibling repositories

## Development status

Implementation is in progress. The database starts empty; schema and seed data are owned by Laravel migrations. The intended developer workflow is a single Compose command from this repository.

Configuration and credentials must come from environment variables. Commit only safe example values; never commit real secrets.

## Related repositories

- [Product specification](https://github.com/code-sena/test-manager-library-3145555-docs)
- `test-manager-library-3145555-api` — Laravel backend and migrations
- `test-manager-library-3145555-app` — React interface
- `test-manager-library-3145555-tool` — API-based demo-data seeder
