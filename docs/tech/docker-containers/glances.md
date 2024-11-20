---
title: Glances
---

Glances is a monitoring tool that allows real-time monitoring of various aspects of your system such as CPU, memory, disk, network usage, running processes, logged in users, temperatures, voltages, fan speeds etc.

## Resources

- [GitHub](https://github.com/nicolargo/glances)
- [Official Documentation](https://glances.readthedocs.io/en/latest/)

## Prerequisites

In the server root directory, create a folder called `glances`. `cd` into it and create the file `docker-compose.yml`.

For instructions on how to use Glances as a widget on Homepage, please see [Setup on Homepage]() (To do...)

## Docker Compose

```yaml title="docker-compose-yml"
---
services:
  glances:
    container_name: glances
    image: nicolargo/glances:4.1.2.1-full
    restart: unless-stopped
    ports:
      - 61208:61208
    environment:
      - TZ=Europe/Stockholm
      - GLANCES_OPT=-w # Glances option to run as a web server
    pid: host # Use the host's PID namespace
    volumes:
	  # Docker socket for monitoring
      - /var/run/docker.sock:/var/run/docker.sock:ro 
```

### Configuration

- **Ports** -	Select an avaliable port for the UI.
- **Environment**

    - `TZ` - Set your local timezone.
    - `GLANCES_OPT=-w`: Run Glances as a webserver.

- **PID** - `pid: host`: Use the host's PID namespace

## Deploy the container

Run the Docker Compose file as a stack in Portainer or with:

```bash
docker compose up -d
```

## Login

**UI:** http://server-ip:61208

## API

To check if the IP works, you can run this code:

```bash
curl http://server-ip:61208/api/4/status
```

You should then get a JSON response like:

```json
{"version":"4.1.2"}
```

Refer to the [documentation](https://glances.readthedocs.io/en/latest/api.html) for what requests are available.