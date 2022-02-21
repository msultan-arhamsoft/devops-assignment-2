# Assignment 2 Submitted by Mahmood Sultan

Use the same github repo as used in Assignment1 or create another repo and type the answers/commands for following scenarios and merge them to main branch from a PR
### Explain Docker Containers vs VMs ###
- Docker containers are process-isolated and don’t require a hardware hypervisor. This means Docker containers are much smaller and require far fewer resources than a VM.
- Docker is fast. While a VM can take an at least a few minutes to boot and be dev-ready, it takes anywhere from a few milliseconds to (at most) a few seconds to start a Docker container from a container image.
- Containers can be shared across multiple team members, bringing much-needed portability across the development pipeline. This reduces ‘works on my machine’ errors that plague DevOps teams.

### Explain Docker Architecture ###
Docker architecture consists of 3 components:
1- Client: Client is a CLI tool. It is a way to interact with Docker daemon.
2- Daemon: Daemon manages the containers. It is runs on the host OS.
2- Daemon: Daemon manages the containers. It is runs on the host OS.
3- Repository: Docker repository contains and ships the images.

### Write command to create an nginx container in detached mode with name assignment-2 running on host port 9090 on a custom network named assignment-2 ###
- First we need to create network by following command.
docker network create assignment-2
- Now we need to run the container on the network we created in the previous command.
docker container run --net assignment-2 --name assignment-2 -d -p 9090:80 nginx

### Write command to see logs of the above container ###
- docker container logs assignment-2

### Write commands to Exec into the container and cat the output of the default nginx file at /usr/share/nginx/html/index.html ###
- docker exec assignment-2 cat /usr/share/nginx/html/index.html

### Exit the above container, and now recreate the container by Volume using bind mounting ###
- Exit and remove the contaier name assignment-2
docker container rm -f assignment-2

- Recreate container using Bind Mounting
docker run -d --name assignment-2 -v assignment-2:/usr/share/nginx/html/ nginx:latest

### Command to exec into the above container and replace the default index.html to a custom one, which says that â€œI am becoming a Docker Expertâ€ and it should be persisted for the next times ###
