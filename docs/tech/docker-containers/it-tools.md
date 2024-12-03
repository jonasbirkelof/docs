---
title: IT-Tools
---

Useful tools for developer and people working in IT.

## Resources

- [https://github.com/CorentinTh/it-tools](https://github.com/CorentinTh/it-tools)

## Prerequisites

In the server root directory, create a folder called `it-tools/`. `cd` into it and create the file `docker-compose.yml`.

## Docker Compose

```yaml title="docker-compose.yml" linenums="1"
---
services:
  it-tools:
    image: corentinth/it-tools:2024.10.22-7ca5933
    container_name: it-tools
    restart: unless-stopped
    ports:
      - 8080:80
```

### Configuration

- **Ports** -	Select an avaliable port for the UI.

## Deploy the container

Run the Docker Compose file as a stack in Portainer or with:

```bash
docker compose up -d
```

## Login

**UI:** http://server-ip:8080