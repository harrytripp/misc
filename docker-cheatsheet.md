# Docker Cheatsheet

## Common Docker Commands

### Identifying Running Containers by Port
To identify the container running on a specific port, use:
```sh
$ docker ps
```
This command lists all running containers along with their port mappings.

### Stopping a Container
Once you've identified the container, you can stop it using:
```sh
$ docker stop <container-name-or-id>
```
Replace `<container-name-or-id>` with the actual name or ID of the container you want to stop.

### Removing a Container
To completely remove the container, use:
```sh
$ docker rm <container-name-or-id>
```

### Stopping All Running Containers
To stop all running containers:
```sh
$ docker stop $(docker ps -a -q)
```

### Removing All Containers
To remove all containers:
```sh
$ docker rm $(docker ps -a -q)
```

### Accessing a Running Container
To access the shell of a running container:
```sh
$ docker exec -it <container_id> /bin/bash
```

### Listing Files Inside a Container
To check the contents of a directory inside a container:
```sh
$ ls /usr/share/nginx/html
```

### Building a Docker Image
To build a Docker image from a Dockerfile:
```sh
$ docker build -t my-nginx-image .
```

### Running a Docker Container
To run a Docker container from an image:
```sh
$ docker run -d -p 8080:80 my-nginx-image
```

### Restarting the Docker Daemon on Fedora
To start, restart, or stop the Docker Daemon on Linux, use:
```sh
$ sudo systemctl start docker
$ sudo systemctl restart docker
$ sudo systemctl stop docker
```

### Find all Docker Packages on Fedora
```sh
$ rpm -qa | grep docker
```

### Deep clean Docker system
Removes:
- All stopped containers
- All networks not used by at least one container
- All dangling and unused images
- All build cache
```sh
$ sudo docker system prune -a
```
