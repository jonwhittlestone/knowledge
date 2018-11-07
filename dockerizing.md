# Dockerizing For SFH / Chris Fidao

https://github.com/shipping-docker/dockerized-app

## Video 1 - Intro

Before we get into CI with docker, dockerizing a Laravel app

Development workflow and CI is as easy as poss

## Video 2 - Existing Laravel app

https://github.com/shipping-docker/dockerized-app

## Video 3 - Making docker images

One for APP     # contains nginx, supervisor
One for Node

Nginx has to actually see the code (php files) so two separate containers for php and nginx which you have to do a volume mount and share

Use a build script and set the context so docker knows where to find files that might be referenced in the Dockerfile

13m54s: docker run --rm -it -p 80:80 -v $(pwd):/var/www/html shippingdocker.com/app

## Video 4 - Creating the Docker compose file

 Run commands using our own container
 
 Going through the docker-compose.yml file
 
 Uses a redisdata volume to persist
 
04m23s: composer install and sets the working directory in docker-compose command
    {{{{{{}}{{{
    docker-compose -f docker-compose.video-4.yml run --rm -w /var/www/html \
        app  \
        composer install
    }}} 

Create .env file with name of services /  php artisan key:generate

## Video 5 - Env files to enable sharing of docker containers and have the user specify the ports to use 

Docker compose environment variables

ports:
    - "${APP_PORT}"

### To reset the ports
$ APP_POST=80 MYSQL_PORT=3306 \
docker-compose down

## Video 6 - Bash script for develop/CI

EG
$ ./develop run --rm -w         # patches though to docker-compose

## Video 7 - more shortcuts

$ develop art route:list

Add for composer, gulp etc

## Video 8 - Add environment vars for DB creds

 `networks:` and `volumes:` defined in extended docker-compose files not docker-compose.base.yml
 
 docker-compose.ci.yml
 
What do we do the ./develop command to specify which docker-compose.yml file to use 
 
 Uses Jenkins and passes through build number
 
 ## Video 9 - using Jenkins
 
 Docker compose adds sudo tty - so that output can be interactive. The same `docker run -it`
 
 ## Video 9 - 
 
 `docker-compose -T` becomes non-interactive so we don't get errors on CI
 
 For interacting with phpunit, can add new command that uses `docker exec` so a new docker container is spun up each time and use one that's already running
