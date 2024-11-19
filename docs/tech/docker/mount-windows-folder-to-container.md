---
title: Mount a Windows folder to a Docker Container
---

If you have to access files, like config files, and make changes to them in production, you will have to mount the local folder directly to the Docker container. This is however not recommended if it can be avoided due to security reasons.

In this example we mount the folder `C:\app_data\` to the container.

```yaml
---
services:
  app:
    volumes:
      - '/c/app_data:/data'
```

Just be aware that the folder `C:\app_data` is now being used live and is read by the Docker container. It is better to avoid this usecase if it's possible!