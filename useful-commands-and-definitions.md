# Batteries Included, But Removable"

docker container top <container_name>  # process list in one container
docker container inspect <container_name> # details of one config container
docker container stats # performance stats for all containers

docker container run -it <container_name># start new container interactively
docker container exec -it <container_name># run additional command in existing container

docker container -ai <container_name> # start interactively an already closed container with everything unchanged in it

docker image ls # list of all images available locally
docker pull <image_name> # downloads an image locally 
	ex: 
	docker container run -it alpine

## Docker Networks
docker container run -p <port_number> # expose a port on the your host using your network;run container on port <port_number>
docker container port <container_name> # quick port check for a given container
	ex: 
	docker container run -p 80:80 --name webhost -d nginx
	docker container port webhost
	80/tcp -> 0.0.0.0:80

	ex:
	docker container inspect --format '{{ .NetworkSettings.IPAddress }}' webhost

## Docker Networks: CLI Management
docker network ls  # show networks
docker network inspect <network_name> # inspect a network
docker network create --driver <network_name> # create a network
docker network connect # attach a network to a container
docker network disconnect # deatach a network from a container

	ex:
	#create a new network 
	docker network create test_network

	#assign/connect 
	docker network connect test_network webhost

	#test if the container is connected to the new network
	docker network inspect test_network # and check the "Containers": part of the JSON
	
	
	#disconnect
	docker network disconnect test_network webhost
### Docker DNS
** Docker daemon has a built-in DNS server that containers use by default

Docker �defaults the hostname to the container's name, but you can also set aliasess
Containers shouldn't rely on IP's for inter-communication



## Docker Images

* app binaries and dependencies
* metadata about the image data and how to run the image
* not a complete OS: no kernel, kernel modules(drivers): because the host machine provides all that
* small as one file (your app binary) like a golang static binary
* big as Ubuntu distro with apt, and Apache, PHP, and more installed

### Image Cache
docker images ls
docker history nginx:latest # show layers of changes made in image
docker image inspect nginx  # default metadata about the image

** Images are made up of file system changes and metadata **
** Each layer is uniquely identified and only stored once on a host **
** This saves storage space on host and transfer time on push/pull ** 
** A container is just a single read/write layer on top of imagee **



## Docker Hub
* hub.docker.com # the apt package system for containers
* official images and how to use them 
* how to discern 'good' public images









