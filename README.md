# Manager Library Infrastructure

Docker Compose starts PostgreSQL 16, the Laravel API, and the React app. PostgreSQL starts with no library tables; the API runs the migrations and provisions the administrator on its first start.

## Start locally

1. Copy `.env.example` to `.env`.
2. Set unique values for `APP_KEY`, `DB_PASSWORD`, `JWT_SECRET`, and `ADMIN_PASSWORD`. `APP_KEY` must be `base64:` plus a Base64-encoded 32-byte key. Keep `.env` private.
3. Run `docker compose up --build` from this directory.
4. Open `http://localhost:8081`; the browser app forwards `/api/v1` to the internal Laravel service.

The database uses a named volume and survives container restarts. `docker compose down -v` deletes the database volume and all stored library data. For a public deployment, terminate HTTPS at a trusted reverse proxy and provide deployment-grade secrets before exposing the app. The API service is not published directly to the host.

## Services

| Service | Purpose |
|---|---|
| `db` | PostgreSQL 16 with a persistent volume |
| `api` | Laravel migrations, admin provisioning, and JSON API |
| `app` | Static React build served by Nginx, with API reverse proxy |

See the [business specification](https://github.com/code-sena/test-manager-library-3145555-docs) for the data and HTTP contract.
