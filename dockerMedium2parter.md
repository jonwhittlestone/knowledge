# Medium 2-part Docker tutorial

* Docker for development - https://medium.com/@shakyShane/laravel-docker-part-1-setup-for-development-e3daaefaf3c
* Docker for Prod - https://medium.com/@shakyShane/laravel-docker-part-2-preparing-for-production-9c6a024e9797
* I tagged 'app' and 'web' images with `▶ docker build -t howapped/yojoe-app -f ./app.dockerfile . `
* `docker build -t howapped/yojoe-web -f ./web.dockerfile .`

Extra server steps
1. Created a test lightsail VPS
    ssh -i ~/.ssh/jon-ca-tm-main-lightsail.pem ubuntu@52.91.247.226
2. Installed docker and docker-compose on lightsail: https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-14-04
3. Retagged the imaages and pushed to my own namespace - https://hub.docker.com/u/jonwhittlestone/
4. Run `docker-compose -f docker-compose.prod.yml up`  and visit in browser
