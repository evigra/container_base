# CONTAINER

This repository contains the template to generate the containers

------------------

# GITHUB CONFIGURATION 
git clone git@github.com:evigra/container_base.git

eval "$(ssh-agent -s)"; ssh-add ~/.ssh/e.vizcaino@solesgps.com
git remote set-url origin git@github.com:evigra/container_base.git


# DOCKER CONTAINER CONFIGURATIONS

sudo chown $(whoami):$(whoami) /var/run/docker.sock

docker network create postgres_16_network

docker-composer up
docker-composer down
docker-composer start
docker-composer stop

# show container in console
docker exec -it container_base18 /bin/bash

docker stop container_base
docker rm container_base 
clear
