# Simple Notes App for TWS Community
This is a simple notes app built with React and Django.

## Requirements
1. Python 3.9
2. Node.js
3. React

## Installation
1. Clone the repository
```
git clone https://github.com/AliFareed0009/Docker-for-DevOps.git
```

2. Build the app
```
docker build -t notes-app .
```

3. Run the app
```
docker run -d -p 8000:8000 notes-app:latest
```

## Nginx

Install Nginx reverse proxy to make this application available

`sudo apt-get update`
`sudo apt install nginx`

## To run with Docker Compose 

Install docker compose then crate a network notes-app-wa with this you can run this application with command

`sudo install docker compose`
`docker network create notes-app-wa -d bridge`
`Follow the below link if you are running this on you local Machine or check the link in terminal` (http://0.0.0.0:8000)
