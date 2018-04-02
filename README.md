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

## Container
A runnable process and its resource dependencies grouped together into a single unit (see above)

## Image
A blueprint for creating containers. Much like class versus object, or VM image versus a VM. As an example, the Redis Docker Image allows you to create one or more actual Redis containers that can/will run the Redis process and whatever dependencies it has.

## Dockerfile
A text file containing instructions for building a docker image. All images have an associated Dockerfile.

## Registry
An external service for storing/referencing images that you can name and version. Dockerhub is a registry provided to you by Docker, but you can set up a private one if need be.

## Volume
Like a traditional Linux mount, a volume is a folder on the docker host system that is mapped into a running container 
  
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
  
