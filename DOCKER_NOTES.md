# Docker Notes — Session 1

## Date
June 2026

## Concepts Learned

### Images
- An image is a blueprint Docker uses to create containers
- Images are downloaded from Docker Hub using `docker pull`
- Images are read-only — they never change when you run them
- Images are made of layers — each instruction in a Dockerfile creates a layer
- What you download from Docker Hub is an image

### Containers
- A container is a live running instance of an image
- You can run many containers from the same image
- Each container is isolated — what happens inside does not affect others
- Stopping a container does not delete it
- Deleting a container does not delete the image

### Dockerfiles
- A Dockerfile is a plain text file with instructions to build an image
- Common instructions: FROM, RUN, COPY, WORKDIR, ENV, EXPOSE, CMD

## Commands Practiced

### Images
docker pull ubuntu          # download ubuntu image
docker pull nginx           # download nginx image
docker pull node:18         # download node version 18 image
docker images               # see all images on your machine
docker history ubuntu       # see layers of an image

### Containers
docker run -d --name mywebserver -p 8080:80 nginx   # run nginx in background
docker ps                   # see running containers
docker ps -a                # see all containers including stopped
docker stop mywebserver     # stop a running container
docker rm mywebserver       # delete a container
docker start container1     # start a stopped container
docker exec -it container1 bash   # get inside a running container

## Hands-On Done
- Ran nginx container and served it on http://localhost:8080
- Confirmed container running with docker ps
- Stopped and removed the container
- Started old ubuntu container and explored filesystem with ls
- Brought back making_boxes-dockerfile-lessons-1 app on http://localhost:3000

## Key Lessons
- docker run creates a brand new container from an image
- docker exec gets inside a container that is already running
- docker ps shows only running containers
- docker ps -a shows all containers including stopped ones
- Removing a container never removes the image
- Containers running locally are only accessible on your machine
- To expose an app to the world you need to deploy to a server like AWS EC2
