
# Docker-for-DevOps


# This Repository is for Docker Containerization Practice 

This Repository is made to practice Docker in and implement daily life scenarios of a Devops Engineer.

## Folders

#### 

| Folder Name | Useages     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `Java_Sample_App` | `Java Application` | A simple application which shows current time |
| `Python_Flask_App` | `Python Application` | A simple application which show health of the server |
| `React_Web_App` | `React Application` | A simple Web Application which shows Welcome Page of React js  |
| `Two-Tier_Flask_App` | `Flask & MySQL Application` | A simple todo application with mysql database connected |

# The Following are topics covered in this Repository

## Introduction
- Docker is an open-source centralized platform designed to create deploy and run applications.
- Docker uses the container on the host O.S to run applications. It allows applications to use the same Linux Kernel as a system on the host computer,rather than creating a whole virtual O.S.

## Docker Architecture
  ![Docker Architecture](/https://github.com/AliFareed0009/Docker-for-DevOps/tree/a1fe1cd115a33162ace3770391af4f029c8a4bda/Images)

# Docker Images
- Docker images are the read-only binary templates used to create docker containers. or, a single file with all dependencies and configurations required to run a program.

### Ways to create an images
- Take an image from Docker Hub.
- Create an image from Docker File.
- Create an image from existing docker containers.

# Docker Container
- The container holds the entire package that is needed to run the application.
- The image is a template and the container is a copy of that template.

# Docker Commands
- docker images - see all images
- docker ps - see running containers 
- docker ps -a - see all containers
- docker build -t <image_name> - to build image
- docker run <container_name> - to start/run a container 
- docker stop <container_name> - to stop a container
- docker rm <container_name> - to delete a container
- docker image rm <imaage_name> - to delete an image
- docker run -itd --name <container_name> <image_name> - to run a container in a de-attach mode

# DockerFile
- Dockerfile is a text file it contains some set of instruction
- Automation of docker image creation

## Creation of  Dockerfile

- FROM : For the base image. This command must be on top of the docker file.
- WORKDIR : To set a working directory for a container.
- COPY : Copy files from the local system (dockerVM) we need to provide a source, and destination. (We can’t download the file from the internet and any remote repo)
- RUN : To execute commands, it will create a layer in the image.
- EXPOSE : To expose ports such as port 8080 for tomcat, port 80 for Nginx, etc…
- CMD : Execute commands but during container creation.
- ENTRYPOINT : Similar to CMD, but has higher priority over CMD, the first commands will be executed by ENTRYPOINT only.

### Steps to create a Docker file

    1. Create a file named Dockerfile
    2. Add instructions in Dockerfile
    3. Build dockerfile to create an image
    4. Run image to create the container

# Docker Networking
- Docker Networking is used to communicate two or more containers with each other.

### Steps to create a docker network

    1. docker network create <network_name> -d bridge
    2. docker run -d --name <container_name> --network <network_name> <imaage_name>
    3. docker network ls
    4. docker network inspect <network_name>

# Docker Volumes and Storage
- Docker Networking is used to communicate two or more containers with each other.

### Steps to create a docker Volumes

    1. docker volume create <volume_name>
    2. docker volume inspect <volume_name>
    Check the Mountpoint in inspect
    3. docker run -d --name <container_name> -v <volume_name>:/var/lib/mysql
    4. docker volume ls

# Docker Compose
# Docker registry
# Multi-Stage Docker Builds
# Monitoring and Logging in Docker
# Orchestrating Docker with Kubernetes ( Introduction )

## Mini_Projects

- Project_1 : Java_Sample_App
- Project_2 : Python_Flask_App
- Project_3 : React_Web_App
- Project_4 : Two-Tier_Flask_App

## Projects

- Project_1 : 3 Tier Application with Docker Compose
- Project_2 : Deploying a Web Application with Nginx and MySQL












