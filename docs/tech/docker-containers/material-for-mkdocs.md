---
title: Material for MkDocs
---

Material for MkDocs is a documentation framework made for MkDocs and is build with Python. It offers a lot of functionallity and customization to you project as well as easy deployment to Docker, GitHub Pages and GitLab Pages.

[Instructions on how to use and setup a local development environment](../material-for-mkdocs.md).

## Resources

- [Material for MkDocs documentation](https://squidfunk.github.io/mkdocs-material/getting-started/)

## Prerequisites

In the server root directory, create a folder called `my-site`. `cd` into it and create the files `docker-compose.yml`, `Dockerfile`, `mkdocs.yml` and the folder `docs/`.

If you will be running Docker on WSL2 on Windows and use that as your server, the `my-site/` folder can be created where it is appropriate, for instance: `C:\prod\my-site`.

To make the site load when the service is running you have to add at least this code to the `mkdocs.yml` file:

```yaml title="mkdocs.yml" linenums="1"
site_name: My Site
site_url: https://mydomain.org/mysite
theme:
  name: material
```

## Docker Compose

```yaml title="docker-compose-yml" linenums="1"
---
services:
  mkdocs:
    image: squidfunk/mkdocs-material
    container_name: my-site
    restart: unless-stopped
    ports:
      - 8000:8000
    volumes:
      - ./:/docs
    stdin_open: true
    tty: true
```

### Configuration

- **Ports** -	Select an avaliable port for the website.

- **Volumes** - Since the container needs the `mkdocs.yml` file to run, we have to create that file before we deploy the container. This means that we can't use named volumes.

	!!! warning "Portainer"
		If you use Portainer, you will have to point to where your `my-site/` folder is located on your system. 
		
		- [Mount a Windows folder to a Docker Container](../mount-windows-folder-to-container.md)
		- Mount a Linux folder to a Docker Container (To do...)

	```yml title="Windows example"
	volumes:
	  - /c/prod/my-site:/docs
	```

## Plugins / Dockerfile

If you need to install plugins, you add them in the `Dockerfile` and then build the project before deploying to the container. Read more in the [official documentation](https://squidfunk.github.io/mkdocs-material/getting-started/#with-docker).

```Dockerfile title="Dockerfile" linenums="1"
FROM squidfunk/mkdocs-material
RUN pip install mkdocs-glightbox
```

Build:

```bash
docker build -t squidfunk/mkdocs-material .
```

## Deploy the container

Run the Docker Compose file as a stack in Portainer or with:

```bash
docker compose up -d
```