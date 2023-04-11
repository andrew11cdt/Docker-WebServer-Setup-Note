# Docker-WebServer-Setup-Note
This note has been created from this course: https://www.udemy.com/course/docker-mastery

Offical installing page: https://docs.docker.com/engine/install/

## Install on ubuntu:

```
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
```

> *the -fsSL option together means that curl should fail silently, but show errors if any, and follow HTTP redirects if necessary. This is a commonly used option combination when you want to download a file from a URL and you don't want any unnecessary output or errors.*

Docker Engine: open-source
Docker Desktop: included Engin (VM maybe) closed-source

[hub.docker.com](https://hub.docker.com)
```
docker login
Username:
Password:
```

## Remote docker Engin via ssh tunnel
>SSH: Secure Shell

* docker-cli: for client machine
* docker-engine: for server machine

## Install docker-cli

linux:
```
apt install docker-ce-cli
```
Others:
```
macOS: brew install docker
window: choco install docker-cli
```
Ex:
```
ssh root@143.244.158.151
```
or setup var
```
export DOCKER_HOST=ssh://root@143.244.158.151
```
check connection with cmd: `docker version`

## Docker config and check info

```
docker version
docker info
```
>docker version: short info for cli and ser machine info
>docker info: details info about machines

```
docker
```
New management cmds format:
>docker <command> <sub-command> (options)

    Old(still works):
>docker <command> (options)

    
ex new vs old format:
```
docker container run
docker run
```

# Nginx Web Server
## Setup Nginx
```
docker container run --publish 80:80 nginx
```
1. Download image 'nginx' from docker hub
2. Start a new container from that image
3. Open port 80 on the host IP
4. Routes that traffic to the container IP, port 80

ex run other port: 8080:80 or 8888:80
then use localhost:888 when testing
## Running in bg
```
docker container run --publish 80:80 --detach nginx
```
>--detach: bg running
## List all containers
```
docker container ls -a
```
> -a list all created containers
> without -a, only running container will be listed
## Stop a container
```
docker container stop <id>
```
><id> could be 3 first digits of id (ex: 4756dc710294 -> docker container stop 475)
## Naming container
```
docker container run --publish 80:80 --detach --name webhost nginx

```
> --name webhost: set container name as webhost
## Show logs for specific container
```
docker container logs webhost
```
    
## All processes running on webhost container
```
docker container top webhost
```
## Remove container
```
docker container rm <id> <id2> <id3>
```
> A running container can't be removed for the sake of safty
