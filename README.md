# CONTAINER

This repository contains the template to generate the containers

------------------

# GITHUB CONFIGURATION 


eval "$(ssh-agent -s)"; ssh-add ~/.ssh/e.vizcaino@solesgps.com
git remote set-url origin git@github.com:evigra/container_base.git

git clone --recurse-submodules https://github.com/evigra/container_base.git

git submodule add git@github.com:evigra/instance_proyecto.git addons/instance_proyecto



# DOCKER CONTAINER CONFIGURATIONS

sudo chown $(whoami):$(whoami) /var/run/docker.sock

docker network create postgres_16_network

docker-composer up
docker-composer down

# Install modules
docker exec -ti container_base18 bash -c "/usr/bin/odoo -i instance_solesgps -p 8008 -d www16 --gevent-port=8672 --db_host db --db_port 5432 --db_user odoo --db_password odoo --without-demo all"

docker exec -ti container_base18 bash -c "/usr/bin/odoo -u instance_solesgps,gpsmap,gpsmap_engine -p 8008 -d www165 --gevent-port=8672 --db_host db --db_port 5432 --db_user odoo --db_password odoo --without-demo all"

# show container in console
docker exec -it container_base18 /bin/bash


docker stop container_base18 db16
docker rm container_base18 db16 
clear

