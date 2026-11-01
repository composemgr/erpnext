## 👋 Welcome to erpnext 🚀

Open-source ERP system built on Frappe Framework

## 📋 Description

Open-source ERP system built on Frappe Framework

## 🚀 Services

- **frontend**: frappe/erpnext:latest

### Infrastructure Components

- **backend, configurator, create-site, websocket, queue-long, queue-short, scheduler**: frappe/erpnext:latest
- **db**: MariaDB database
- **redis-cache, redis-queue**: Redis cache and job queue


## 📦 Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/erpnext/main/docker-compose.yaml" -o compose.yml
```

### Option 2: Git Clone
```bash
git clone "https://github.com/composemgr/erpnext" ~/.local/srv/docker/erpnext
cd ~/.local/srv/docker/erpnext
cp default.env .env
docker compose --env-file .env up -d
```

### Option 3: Using composemgr
```bash
composemgr install erpnext
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=America/New_York
APP_ORG_NAME=ERPNext
DB_ADMIN_NAME=root
DB_ADMIN_PASS=replace-with-a-random-password
EMAIL_SERVER_MAIL_FROM=no-reply@example.com
```

See `docker-compose.yaml` for complete list of configurable options.

### Environment Files

`default.env.sample` holds the full set of variables and is copied to `.env`
before starting the stack:

```bash
cp default.env .env
docker compose --env-file .env up -d
```

`app.env.sample` holds the app-specific overrides and is copied to `app.env`:

```bash
cp app.env.sample app.env
```

`composemgr up` applies `app.env` and `default.env` automatically. Raw
`docker compose` commands need `--env-file .env` to pick up the same values.

### Reverse Proxy

Three standalone compose files ship in this repo:

| File | Use |
|------|-----|
| `docker-compose.yaml` | Default, published on `172.17.0.1:64166` |
| `docker-compose.traefik.yaml` | Behind an existing external `traefik` network |
| `docker-compose.tunnel.yaml` | Behind an existing external `cloudflare` tunnel network |

```bash
docker compose -f docker-compose.traefik.yaml --env-file .env up -d
```

## 🌐 Access

- **Web Interface**: http://172.17.0.1:64166

## 📂 Volumes

- `./volumes/data/erpnext/sites` - ERPNext sites and app files
- `./volumes/data/erpnext/logs` - Bench process and web server logs
- `./volumes/data/redis/erpnext-queue` - Redis queue persistence
- `./volumes/db/mariadb/erpnext` - MariaDB database files


## 🔐 Security

- Change all default passwords before deploying to production
- Use strong secrets for all authentication tokens
- Configure HTTPS using a reverse proxy (nginx, traefik, caddy)
- Regularly update Docker images for security patches
- Backup your data regularly

## 🔍 Logging

```shell
docker compose --env-file .env logs -f erpnext
```

## 🛠️ Management

```bash
# Start services
docker compose --env-file .env up -d

# Stop services
docker compose --env-file .env down

# Update to latest images
docker compose --env-file .env pull && docker compose --env-file .env up -d

# View logs
docker compose --env-file .env logs -f

# Restart services
docker compose --env-file .env restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
