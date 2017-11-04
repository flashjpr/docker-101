docker container top <container_name>  # process list in one container
docker container inspect <container_name> # details of one config container
docker container stats # performance stats for all containers

docker container run -it <container_name># start new container interactively
docker container exec -it <container_name># run additional command in existing container

docker container -ai <container_name> # start interactively an already closed container with everything unchanged in it

docker image ls # list of all images available locally
docker pull <image_name> # downloads an image locally 

ex: docker container run -it alpine
