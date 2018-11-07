# Home Automation Sever Notes

The Beginning: Ubuntu 18.04

Step One.
Set up (VM at first) with

- hass.io (accessible from LAN)
- Plex
- Couchpotato (for bonus points) https://github.com/n8io/ultimate-media-server

Step Two.
- Have each working as docker containers
- Provision the whole process with Ansbile for loading onto new hardware

## Step One
- Install Ubuntu 17.04 Server
- Install OpenSSH Server
    sudo apt-get install -y openssh-server
- Set up [port forwarding]() in Vbox so we can do
    ssh -p22222 jon@127.0.0.1
 - Install Python
    sudo apt-get install -y python3.6
- Install pip3
    sudo apt-get install -y python3-pip
 - Install Docker | https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04
 - Install socat
    sudo apt install socat
- Install jq
    sudo apt install jq
- Install curl
    sudo apt install curl
 - Install other stuff
    sudo apt-get install jq pigz git
 - Build hass.io with:
    https://github.com/home-assistant/hassio-build/tree/master/install#install-hassio
 - To get Hassio running: stop the docker container and restart with port 80 forwarded to 8123
    docker run -d --name="home-assistant-test" -p 80:8123 homeassistant/qemux86-64-homeassistant
    
- Couchpotato docker containers
  
1. Clone to the server,  
    git clone git@github.com:n8io/ultimate-media-server.git
3. 
