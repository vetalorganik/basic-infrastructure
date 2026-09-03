# Basic infrastructure

`postgres:16-alpine` + `valkey:8-alpine` on `vps_net` bridge. Volumes `postgres_data`/`valkey_data` with `:Z` for Podman SELinux.

## Usage

```bash
cp .env.example .env
docker compose up -d        # or podman-compose up -d
docker compose ps           # wait for (healthy)
```

## Override

`docker-compose.override.yml` publishes ports to `127.0.0.1` only.

- **Keep** for local dev (host `psql`/`valkey-cli` access).
- **Remove** in production (apps use `vps_net`, no host ports) or CI (port conflicts).

Bypass: `docker compose -f docker-compose.yaml up -d`
