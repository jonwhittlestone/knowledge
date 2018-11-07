# Docker Cheatsheet

Picked up from here and there on the web

* Docker system size / capacity
    
    docker system df
    
* Rebuild docker-compose containers

    docker-compose build
    
* Remove all images
    
    docker images -q | xargs docker rmi
    
* Kill all docker containers
    
    docker ps -q    
    
* Stop all Docker containers
    
    docker stop $(docker ps -a -q)
    
* Remove all docker containers
    
    docker rm $(docker ps -a -q)
    
* SSH into a container
    
    docker exec -it <container_name> /bin/bash
    
* Connecting to a postgres container from host
    
    psql -h 192.168.99.100 -p 5432 -U postgres --password
