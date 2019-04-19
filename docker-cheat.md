### Generic info

	docker --version
	docker version
	docker info


### Run a local image or download it and run

	docker run hello-world
	docker run -d -p 80:8081 exampleapp:v0.0.1
	docker stop hello-world
**TODO run without pull**

### List Docker images or containers

	docker image ls
	docker images
	docker container ls        # running containers
	docker container ls --all  # all containers


### Delete o remove image container
	
	docker system prune             # clean up images and containers
	docker image rm e53eae898fe7
	docker image rm hello-world -f
	docker rm container
	docker rmi <image>
	docker rmi $(docker images -f "dangling=true" -q) # remove dangling images


### Build a image (after cd into project dir and create Dockerfile)

	docker build --tag=myapp          # same as myapp:latest (latest version)
	docker build --tag=myapp:v0.0.1


### Create and run container

	docker run -it --rm alpine bash


### Start stop container
	
	docker start <container-id>
	docker stop <container-id>


### Attach and detach running container

	docker ps
	docker attach <container-id-or-name>
	ctr-p ctr-q	   # detach
	
	# sometimes ctrl-p ctrl-q does not work
	sudo docker attach --sig-proxy=false <container> 
	ctrl-c to detach


### Example connecting on running local postgresql 9.1

	docker run -d -p 5555:5432 --name old_postgres postgres:9.1
	docker exec -it old_postgres psql --user postgres


### Container network info after launch some containers or compose
	(https://docs.docker.com/network/network-tutorial-standalone/)

	docker network ls
	docker network inspect <bridge>

	docker exec -it <container> bash
	root@<container>:/# ip addr show


**TODO configure private hub host server**
**TODO configure local machine to pull from configured server**

**TODO ??? recreate container after deploy?**
