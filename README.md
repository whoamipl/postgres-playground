# Postgres playground

This is simple docker-compose file that creates three containers with Postgresql database.
## Prerequisites

On windows you just need to install docker app, but on linux you need install docker and docker-compose separetly.

    apt-get update && apt-get install docker docker-compose 

To run docker without root privileges, you must be in docker group

    usermod -aG docker your_username

Then logout and login and run docker deamon with: 

    sudo dockerd 
or

    sudo systemctl start docker.service

## How to run

In dir where is dockerfile 
    
    docker-compose up -d 

## How to connect to specyfic container 

The containers are working on porst 50090, 50091, 50092. Below command connect you directly to psql cli. 

    psql -h localhost -p 50090 -d docker -U docker --password

If you want do change configuration of database you can run bash shell into container and switch user to postgres.

    docker exec -ti container_id /bin/bash 

To get container id run:

    docker ps

## How to login as root 

    docker exec -u 0 -it mycontainer bash