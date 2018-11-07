# Servers For Hackers

https://app.plex.tv/web/app#!/server/bc0049189e861dd58c943d9c7307957a899ce527/playlist/5595://app.plex.tv/web/app#!/server/bc0049189e861dd58c943d9c7307957a899ce527/playlist/55953

----

## 01 Quickstart

`docker-compose` up on a php app

https://github.com/shipping-docker/php-app

In docker-compose, all services are inside of a network, so we can refer to them by their names E.g in `.env` file, set the db host to be 'db' rather than `127.0.0.1`


	docker-compose 	ps	see a listing of running containers 
	docker compose ps -a	see all containers including exited
	docker compose stop	stop containers but not destroy
	
	running composer inside container	
	
	docker run -it --rm \
	    	-v $(pwd)/application:/opt \
	    	-w /opt \
		--network=phpapp_appnet \
		shippingdocker/php \
		composer require predis/predis
----

## 02 Docker Compose

Services are technically just containers to run
Since in the same network (appnet) - the nginx container is able to resolve to php container name
	- "80:80" This means share port 80 of local computer to port 80 of the container 
The docker container can 'see' the files on your local file system because the volumes key has forwarded the local directory of the computer

	volumes:
	- ./application:/var/www/html

`appnet:` creates a small network that only docker can use and all containers can use to speak to each other. The hostname of the db createor is the name - `db`

The database data will survive a `docker-compose down` because it contains code to reuse any code remaining in the shared volumne

----
## 03 Volumes

Volumes persist data to the local filesystem
Another layer of virtualisation if you're on Mac or Windows

	docker volume ls			list out the current volumes
	docker ps				list out running containers
	docker inspect <hash> | jq		see in the mounts key (is able to see file on your local machine - if it's Linux)
	docker-compose up -d			Brings up in deatched mode (without seeing logs)
	docker start <hash>			starts the container
	docker exec -it root_db_1 bash		Execute interactively bash on the 'root_db_1' container
	
----
## 04 Docker networks

Use default nginx configuration which specifies the `php` host name rather than the hostname IP address

	...
	location ~ \.php$ {
		include snippets/fastcgi-php.conf;
		fastcgi_pass php:9000;
	}


	docker network ls			list out the networks
	docker network inspect	{name}		gives info about the containers that make up the network with actual IP addresses
	dig db					dig any of our services
	
----
## 05 Docker Hub

Use [alpine](https://hub.docker.com/_/alpine/) as a container vendor as images are often v. small

----
## 06 Linux File Permissions

When running docker directly on a linux server

Match the user id of the user that owns the docker processes whereas all application files are probably owned by user `root` so PHP can't write to it / doesn't have permission

 	ps aux		see what processes are running and see what users are owning the processes
	id www-data	to get id of user
	
Set permissions on app files with `chown -R 33 application/` and `chgrp -R docker application/`

----
## 07 Using regular docker commands

To do what `docker-compose` does manually.

Create your own network in addition to the existing defaults
`docker network create --driver=bridge --name=jwnet`

Two containers both sharing the same volume, the change will get reflected in both containers

	docker rm <container_id>		removes a docker container
	
----
## 08 Building Nginx

In [/build](https://github.com/shipping-docker/php-app/tree/master/build) directory for info on how images were built

Dockerfile walk trough / from what docker image to base this on

Analgous to git commit

Advantage is that future changes to an image are very quick so we don't need to build up all every time we build an image. Making a change will start from latest commited images. Quick to update base images in Docker.


	docker images					The images that are located on computer that can be used to start a container
	docker rmi <image_id>				Remove an image
	docker build -t org/imageName:latest		Build the dockerfile it finds with the tag
	docker login					Login to the Docker hub
	docker push org/imageName:latest		To push up to the registry
	docker run -it ubuntu:16:04 bash		Run bash in an Ubnutu image
	
----
## 09 Building PHP

Set to not run as a daemon (in www.conf)

Listen of a network instead of a unix socket file

	listen=0.0.0.0:9000
	
----
## 10 Development Workflow

`Makefile` is like a collection of bash scripts to make the developer's life easier

```
$ vim Makefile
$ make foo
```
Allows to use `php artisan tinker` in a new container
A test container that runs the tests ina container

----
## 11 When you try to ping localhost from your containers

Two containers that handle web requests

The PHP container doesn't have port 80 listening to anything
