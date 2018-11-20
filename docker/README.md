# Dockerfile

Dockefile is created on top of `php:5-apache-jessie` image.

# Quick Start

- Clone the repository on your machine https://github.com/trilogy-group/nextcloud-server
- Open a terminal session to nextcloud-server/docker folder
- Run `git submodule update --init`
- Run `docker-compose build`
- Run `docker-compose up -d`
- Run `docker exec -it nextcloud bash`
- Run `chown -R www-data .`
- The application should be running by now. Navigate to `localhost` from your host to access the web application.
- When you finish working with the container, type `exit`
- Run `docker-compose down` to stop the service.

## Configuring NextCloud
When you run the application first time, it will require some inputs from you. Make sure to provide correct database parameters (which can be found under `nextcloud-server/docker/docker-compose.yml` file. 

## Troubleshooting
Sometimes you might receive 500 error codes. This happens after restarting the container often. Simply delete the content of `config` folder and restart the containers to fix this issue.

## Build the image

In `nextcloud-server/docker` folder, run:

```bash
docker-compose build
```

This instruction will create a docker image in your machine called `nextcloud_builder:latest`

## Run the container

In `nextcloud-server/docker` folder, run:

```bash
docker-compose up -d
```

Parameter `-d` makes the container run in detached mode.
This command will create a running container in detached mode called `nextcloud`.
You can check the containers running with `docker ps`

## Get a container session

Run:

```bash
docker exec -it nextcloud bash
```

Parameters `-it` allocate an interactive TTY session

## docker-compose.yml

The docker-compose.yml file contains both MySQL instance and a service called `builder`, which is used to run the application. 
We will use this service to run nextcloud from our local environment, so we mount root project dir `nextcloud-server` to the a `/var/www/html/` folder:

```yaml
    volumes:
      - ..:/var/www/html/:Z
```

## Requirements
The container was tested successfully on:
- Docker 17.05 and up
- docker-compose 1.8 and up

