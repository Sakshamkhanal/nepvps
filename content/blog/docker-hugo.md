---
title: "Basic Insight into Docker: Running Your First Image into a Docker Container"
date: 2025-08-18
author: "Nabin Lopchan"
description: "A beginner-friendly guide to understanding Docker, pulling your first image, and running it in a container."
categories: ["Docker", "Containerization"]
tags: ["Docker", "Containers", "DevOps", "Linux"]
featured_image: "/images/blog/docker.jpg"
---

{{< toc >}}

## Introduction

Docker is a platform that enables developers to automate the deployment of applications inside lightweight, portable containers. These containers package an application and its dependencies, ensuring consistency across various environments.

In this guide, we'll walk through the process of pulling your first Docker image and running it inside a container.

## Prerequisites

Before we begin, ensure you have:

- Docker installed on your system.
- A basic understanding of Docker concepts like images and containers.

## Step 1: Verify Docker Installation

To confirm Docker is installed and running:

```bash
docker version
```

This command will display the installed Docker version.

## Step 2: Pull a Docker Image

Docker Hub is a public repository where you can find a variety of Docker images. For this example, we'll pull the official NGINX image:

```bash
docker pull nginx
```

This command downloads the latest NGINX image from Docker Hub.

## Step 3: Run the Docker Container

Once the image is downloaded, you can run it as a container:

```bash
docker run --name mynginx -p 8080:80 -d nginx
```

Explanation of the flags:

- `--name mynginx`: Assigns a name to the container.
- `-p 8080:80`: Maps port 80 of the container to port 8080 on your host.
- `-d`: Runs the container in detached mode (in the background).

Now, you can access the NGINX welcome page by navigating to `http://localhost:8080` in your web browser.

## Step 4: Interact with the Running Container

To access the running container's shell:

```bash
docker exec -it mynginx sh
```

This command opens an interactive shell inside the container.

## Step 5: Stop and Remove the Container

To stop the running container:

```bash
docker stop mynginx
```

To remove the container:

```bash
docker rm mynginx
```

## Conclusion

Congratulations! You've successfully pulled a Docker image and ran it inside a container. This is just the beginning—Docker offers a plethora of features to explore, including custom images, Docker Compose, and orchestration with Kubernetes.

For more detailed information, refer to the original Medium article by Nabin Lopchan: [Basic Insight into Docker: Running Your First Image into Docker Container](https://medium.com/@lopchannabeen138/basic-insight-into-docker-running-first-image-into-docker-container-9189c507b29b).
