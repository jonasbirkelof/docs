---
title: Install Docker on Ubuntu
---

This page will explain how to install Docker on Ubuntu. The following steps are taken from the official [Docker website](https://docs.docker.com/engine/install/ubuntu/).

<div class="steps" markdown>

1. Use SSH to connect to the Ubuntu server.

1. Add Docker's official GPG key.

    ```bash
    sudo apt-get update
    sudo apt-get install ca-certificates curl
    sudo install -m 0755 -d /etc/apt/keyrings
    sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
    sudo chmod a+r /etc/apt/keyrings/docker.asc
    ```

1. Add the repository to Apt sources.

    ```bash
    echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
    $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
    sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    sudo apt-get update
    ```

1. Install the latest version of Docker and additional packages.

    ```bash
    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    ```

</div>

To not have to type `sudo` before every docker command, run this script and change `<USERNAME>` to your username:

```bash
sudo usermod -aG docker <USERNAME>
```

Log out using `logout` and log in again for the changes to take effect.