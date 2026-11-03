# Configuration

| File | Description |
| ---- | ----------- |
| `docker-compose.yml` | Greenbone Community Edition 24.10 stack (scanner, gvmd, gsad, PostgreSQL, Redis, Nginx, feed containers) |

## Run the stack

```bash
cd config
docker compose pull
docker compose up -d
docker compose ps
```

The web interface is served by Nginx on `https://<host-ip>` (port 443; port 9392 is also published).
The first start downloads the vulnerability feeds, which can take a long time. Wait until the
feed data containers report `healthy` before creating scans.

## Set the admin password

```bash
docker compose exec -u gvmd gvmd gvmd --user=admin --new-password='<choose-a-strong-password>'
```

## Stop and clean up

```bash
docker compose down        # stop containers, keep data volumes
docker compose down -v     # stop containers and DELETE all data volumes
```

## Hardening notes

- Ports 443 and 9392 are published on all interfaces. For anything beyond an isolated lab,
  bind them to a management address, e.g. `127.0.0.1:443:443`.
- Several images use the `stable` / `latest` tags. Pin explicit versions or digests for
  reproducible deployments.
- `ospd-openvas` runs with `NET_ADMIN`, `NET_RAW` and unconfined seccomp/AppArmor, as required
  by the upstream stack for raw-socket scanning. Run it only on trusted hosts.
