# CUDA QuickStart

A docker image to quick start your CUDA development

## Docker-compose
To set up this docker image on your machine you can use the following docker-compose.

Fasted way to get it up and running is if you run this in a new directory
```
wget https://raw.githubusercontent.com/solomspd/docker-CUDA/master/docker-compose.yml && docker-compose up -d
```

This will download the following docker compose file and run it

```yaml
---
version: "2.1"
services:
  cuda-starter:
    image: solomspd/cuda-starter
    environment:
      - TZ=Africa/Cairo
      - DEFAULT_WORKSPACE=/home/workspace
    ports:
      - 8443:8443
      - 22:22
    restart: unless-stopped
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: 1
              capabilities: [gpu]

```

To start debugging and building, take a look at the workspace directory that has every you need to get started including a simple build environment and hello world program.

## Build

To build the docker image, you need to clone the repo:
```
git clone --recusive https://github.com/solomspd/docker-CUDA && docker-CUDA
```

Then build the docker image:
```
docker build -t solomspsd/cuda-starter .
```
