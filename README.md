# Docker Cheatsheet

## Basic Docker Commands:
```
docker run <image>
docker start <name | id>
docker stop <name | id>
docker ps [-a include stopped containers]
docker rm <name | id>
```

## Basic Docker Terminology
### Docker Images:  
Blueprints of our application.
### Docker Container: 
Real instances of our application. 
### Docker Deamon: 
Building, running and distributing Docker containers.
### Docker Client: 
Runs on the local machine and connects to the daemon. 
### Docker Hub: 
Registry of docker images. 
  
## Working with Docker& Ubuntu and Node.js
```
docker search ubuntu 
docker run -it ubuntu ./bin/bash
```

### Because there is no package cache in the image, you need to run:
```
apt-get --qq update
apt-get install nodejs
apt-get install nodejs-legacy
apt-get install npm 
```

### In order to create a docker image:
```
docker commit CONTAINER-ID IMAGE-NAME:tag
```

## Create a micro_service:
```
npm install -g express-generator
express micro_service
npm install 
npm start 
```
### In order to run micro_service within the container:
```
docker run -it -v HOSTFOLDER:CONTAINERFOLDER -p HOSTPORT:CONTAINERPORT IMAGENAME:TAG
```
### Copy the micro_service to permanent folder within the container:
```
cp -r CONTAINERFOLDER /PERMANENTFOLDER
cd PERMANENTFOLDER
npm start
```
### Create an image of micro_service and run within the container:
```
docker commit CONTAINERID, IMAGETAG:TAG
docker run -d -w /PERMANENTFOLDER -p HOSTPORT:CONTAINERPORT IMAGENAME npm start
```

## Push to Docker Hub
```
docker login
docker tag nodejs_micro_service DOCKER_USER/nodejs_micro_service
docker push DOCKER_USER/nodejs_micro_service
```
  
