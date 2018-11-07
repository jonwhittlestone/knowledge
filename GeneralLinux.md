# General Linux

* [Init Systems - Digital Ocean](https://goo.gl/bru87d)
* [ssh](ssh) 
* []BlankWorkUbuntuServerForWork](blankubuntu.md)
* [Networking Linux](networkinglinux.md)

----
## Converting to Ubuntu ## 

* check version of ubuntu
    cat /etc/lsb-release
    
* install docker
    https://www.howtoforge.com/tutorial/ubuntu-docker/
    
* mounting NAS to /home/jon/nas

    sudo mount -t cifs -o username=jonwhittlestone //192.168.17/jonwhittlestone /home/jon/nas/
    
* copy/paste between tmux windows
    1. go to vim in pane 1
        * CTRL + B + [
        * SPACE to select
        * ENTER to copy into tmux clipboard
    
    2. go to vim in pane 2
        * insert mode
        * CTRL + B + ]

* install PHP7.2

* install Xdebug

* install systemd services to start at boot: http://bit.ly/2D25Ig7 | http://bit.ly/2CYHHXa
 
* Install dbeaver-ce SQL editor
* Install postgres
    * https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-18-04
