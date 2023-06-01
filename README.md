# Automad

The official Docker image for [Automad](https://automad.org) including **Nginx** and **PHP 8.1**.

[![Build Docker Image](https://github.com/marcantondahmen/automad-docker/actions/workflows/build.yml/badge.svg?branch=master&event=schedule)](https://github.com/marcantondahmen/automad-docker/actions/workflows/build.yml)

## Using this Image

You can create a container called `mysite` and start it by using the following command:

```bash
docker run -dp 80:80 -v ./app:/app --name mysite automad/automad
```

This will essentially make your site available at port 80 and mount a directory called `/app` for data persistence.
A new user account for the Automad dashboard will be created automatically. The account details will be logged by the running container. You can show these logs using the following command:

```bash
docker logs mysite
```

Your can now navigate to [localhost](http://localhost) to view your new site.

### Docker Compose

Alternatively you can also use `docker compose` with the following configuration:

```yaml
version: "3"
services:
  app:
    container_name: automad
    image: automad/automad:latest
    ports:
      - 80:80
    volumes:
      - ./app:/app
```

And then in order to start the container:

```bash
docker compose up -d
```
