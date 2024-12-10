
# Docker-for-DevOps


# This Repository is for Docker Containerization Practice 

This Repository is made to practice Docker in and implement daily life scenarios of a Devops Engineer.

## Folders

#### 

| Folder Name | Technologies     | Useages & Description                       |
| :-------- | :------- | :-------------------------------- |
| `Java_Sample_App` | `Java Application` | A simple application which shows current time |
| `Python_Flask_App` | `Python Application` | A simple application which show health of the server |
| `React_Web_App` | `React Application` | A simple Web Application which shows Welcome Page of React js  |
| `Two-Tier_Flask_App` | `Flask & MySQL Application` | A simple todo application with mysql database connected |
| `Nginx_MySQL_Web_Notes_App` | `React & Django Application` | A simple Web application to take notes with mysql database |
| `Three_Tier_Expenses_Tracker_App` | `Java, Spring Boot & MySQL Application` | A simple Expense Tracker application |

# The Following are topics covered in this Repository

## Introduction
- Docker is an open-source centralized platform designed to create deploy and run applications.
- Docker uses the container on the host O.S to run applications. It allows applications to use the same Linux Kernel as a system on the host computer,rather than creating a whole virtual O.S.

## Docker Architecture
  ![Docker Architecture](https://github.com/AliFareed0009/Docker-for-DevOps/blob/main/Images/Architecture.png?raw=true)

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
- docker images - To see all images
- docker ps - To see running containers 
- docker ps -a - To see all containers
- docker build -t <image_name> - To build image
- docker run <container_name> - To start/run a container 
- docker stop <container_name> - To stop a container
- docker rm <container_name> - To delete a container
- docker image rm <imaage_name> - To delete an image
- docker run -itd --name <container_name> <image_name> - To run a container in a de-attach mode
- docker rm -vf $(docker ps -aq) - To delete all containers including its volumes forcefully
- docker rmi -f $(docker images -aq) - To delete all the images forcefully
- docker compose up - To start the containers in compose-yaml file
- docker compose down - Stop and remove all the containers

# DockerFile
- Dockerfile is a text file it contains some set of instruction
- Automation of docker image creation

 ![Docker File](https://github.com/AliFareed0009/Docker-for-DevOps/blob/main/Images/DockerFile.png?raw=true)

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
- Volumes are persistent data stores for containers, created and managed by Docker.
- When you create a volume, it's stored within a directory on the Docker host. When you mount the volume into a container, this directory is what's mounted into the container. Volumes are managed by Docker and are isolated from the core functionality of the host machine.

### Steps to create a docker Volumes

    1. docker volume create <volume_name>
    2. docker volume inspect <volume_name> 
    
    Check the Mountpoint in inspect
    3. docker run -d --name <container_name> -v <volume_name>:/var/lib/mysql
    
    4. docker volume ls
    5. docker volume rm <volume_name>

![Docker Volume](https://github.com/AliFareed0009/Docker-for-DevOps/blob/main/Images/Volumes.png?raw=true)

# Docker Compose
- Docker Compose is a tool for defining and running multi-container applications. It is the key to unlocking a streamlined and efficient development and deployment experience.
- Compose simplifies the control of your entire application stack, making it easy to manage services, networks, and volumes in a single, comprehensible YAML configuration file. Then, with a single command, you create and start all the services from your configuration file.

### Steps to Run docker Compose
    To Install docker compose run the below command
    1. sudo apt-get install docker-compose-v2

    To start all the services defined in your compose.yaml file:
    2. docker compose up

    To stop and remove the running services:
    3. docker compose -d

    If you want to monitor the output of your running containers and debug issues, you can view the logs with:
    4. docker compose logs

    To lists all the services along with their current status:
    5. docker compose ps

# Docker registry
    First rename the docker image in docker regitry format
    1. docker image tag image_name:version DockerHub_username/image_name:version

    After renaming the image now push it to docker registry:
    2. docker push DockerHub_username/image_name:version

    To  pull the image from docker Hub regitry
    3. docker pull DockerHub_username/image_name:version

# Docker Multi-Stage Docker Builds
- With multi-stage builds, you use multiple FROM statements in your Dockerfile. Each FROM instruction can use a different base, and each of them begins a new stage of the build. You can selectively copy artifacts from one stage to another, leaving behind everything you don't want in the final image.

### Multi-Stage DockerFile
        # Dockerfile-multistage
    # ------- stage_1 starts here ------- #

    # This base image python:3.7 with size 1.02GB is used to install packages
    # FROM Base image python and givee this stage a name Builder
    FROM python:3.7 AS builder

    # Make a Working Directory
    WORKDIR /app

    # Copy the requirements to this working directory
    COPY requirements.txt .

    # Install whatever is in requirements.txt file
    RUN pip install -r requirements.txt

    # ------- stage_1 ends here ------- #

    # ------- stage_2 starts here ------- #

    # This base image python:3.7-slim with size 125MB
    FROM python:3.7-slim

    WORKDIR /app

    # Copy the installed package from stage_1 to this final image
    COPY --from=builder /usr/local/lib/python3.7/site-packages/ /usr/local/lib/python3.7/site-packages/

    COPY . .
    
    ENTRYPOINT [ "python3", "run.py" ]

    # ------- stage_2 ends here ------- #

# Monitoring and Logging in Docker
- We can monitor the docker continer with the following command, the output will redirect to a nohup file

### Commands use to create nohup file
    Creates a nohup.out file
    cmd: nohup docker atach container_id $

## Mini_Projects

- Project_1 : Java_Sample_App
- Project_2 : Python_Flask_App
- Project_3 : React_Web_App
- Project_4 : Two-Tier_Flask_App

## Projects

- Project_1 : 3 Tier Application with Docker Compose
- Project_2 : Deploying a Web Notes Application with Django, Nginx and MySQL












