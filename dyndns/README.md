# Dynamic DNS Docker container

## Why?

The docker container format was choosen to utilize the process respawn capability of docker to 
use the inadyn-mt program to dynamically update a DNS alias with your current public IP.
This is quite useful if you have a NAS system or any other server running at home and you want to connect
to it using any dial-up or cable ISP

## How to build the docker image ?

```
git clone https://github.com/BjoernT/docker.git
cd docker && docker build -t 'github/dyndns:latest' dyndns
```

The build should finish within few minutes depending on you cache status of the Fedora base image

```
# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
github              dyndns:latest       3042ec4f15b6        22 minutes ago      616.5 MB
```

## Starting a container

```
# docker run --name dyndns -i -t 'dyndns:latest'
```

## Checking status off inadyn-mt

```
# docker ps -f name=dyndns
CONTAINER ID        IMAGE               COMMAND                CREATED             STATUS              PORTS               NAMES
47f4ffb2a064        3042ec4f15b6        "/bin/sh -c '/usr/sb   25 minutes ago      Up 25 minutes                           dyndns
```

```
# docker logs dyndns
```

A successfull update should look similar to the following message:

```
W:INADYN: Alias 'home.dnsalias.net' to IP '1.2.3.4' updated successfully.
```

