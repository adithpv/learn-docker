# Docker Comprehensive Guide

This document provides a general overview and practical guide for using Docker in software development projects. It is suitable for beginners and intermediate users working with containerized applications.

---

## Table of Contents

-   [What is Docker?](#what-is-docker)
-   [Key Concepts](#key-concepts)
-   [Basic Docker Commands](#basic-docker-commands)
-   [Dockerfile Basics](#dockerfile-basics)
-   [Docker Compose](#docker-compose)
-   [Volumes and Networks](#volumes-and-networks)
-   [Best Practices](#best-practices)
-   [Troubleshooting](#troubleshooting)
-   [References](#references)

---

## What is Docker?

Docker is a platform for developing, shipping, and running applications inside lightweight containers. Containers package code and dependencies, ensuring consistency across environments.

## Key Concepts

-   **Image:** A snapshot of a filesystem and parameters for running a container.
-   **Container:** A running instance of an image.
-   **Dockerfile:** Script to build images.
-   **Volume:** Persistent storage for containers.
-   **Network:** Communication layer between containers.

## Basic Docker Commands

```bash
# Build an image from a Dockerfile
docker build -t <image_name> .

# Run a container from an image
docker run -d -p <host_port>:<container_port> <image_name>

# List running containers
docker ps

# Stop a container
docker stop <container_id>

# Remove a container
docker rm <container_id>

# Remove an image
docker rmi <image_id>
```

## Dockerfile Basics

A `Dockerfile` defines how to build a Docker image. Example:

```Dockerfile
FROM node:18
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

## Docker Compose

Docker Compose allows you to define and run multi-container applications using a `compose.yml` or `docker-compose.yml` file.

Example:

```yaml
version: "3.8"
services:
    app:
        build: .
        ports:
            - "3000:3000"
    db:
        image: mongo
        ports:
            - "27017:27017"
```

## Volumes and Networks

-   **Volumes:** Persist data outside containers.
    ```bash
    docker volume create mydata
    docker run -v mydata:/data <image>
    ```
-   **Networks:** Isolate and connect containers.
    ```bash
    docker network create mynet
    docker run --network=mynet <image>
    ```

## Best Practices

-   Use `.dockerignore` to exclude unnecessary files.
-   Keep images small and use official base images.
-   Tag images with meaningful names and versions.
-   Use environment variables for configuration.
-   Clean up unused images and containers regularly.

## Troubleshooting

-   **Build errors:** Check Dockerfile syntax and paths.
-   **Port conflicts:** Ensure host ports are available.
-   **Permission issues:** Use correct user permissions in containers.
-   **Networking issues:** Verify network configuration and container connectivity.

## References

-   [Docker Documentation](https://docs.docker.com/)
-   [Docker Compose Docs](https://docs.docker.com/compose/)
-   [Awesome Docker](https://github.com/veggiemonk/awesome-docker)

---

For project-specific Docker instructions, see the Docker guides in each subfolder.
