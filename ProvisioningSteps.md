# Provisioning Steps

## Linux Debian
* `sudo pip install vim git`
* [install dotfiles containing vimrc](https://github.com/jonwhittlestone/dotfiles)
* `sudo apt-get install python3 -y`
* `sudo apt-get install -y software-properties common`
* ``sudo apt-getinstall -y python-pip``
* Install glances for monitoring: https://github.com/nicolargo/glances

### RaspberryPi
- Don't use default as pip3, use a venv instead
- Install vim8 for dealing with vim7.4 plugin nags: https://goo.gl/aKDqGq
- Gitaware prompt in bash: https://goo.gl/rBFf7R
- NUC client for noip dns forwarding: https://goo.gl/kv7Tzv
- Install NUC client above as daemon with Systemd: http://neilwebber.com/notes/2016/02/10/making-a-simple-systemd-file-for-raspberry-pi-jessie/

#### Optional

- Install Redis: https://goo.gl/g715I8
- redis-server-for-init.d-startup: https://gist.github.com/lsbardel/257298
    - wget above gist into `wget -O /etc/init.d/redis-server``
    - `chmod 755 /etc/init.d/redis-server`
    - ``update-rc.d redis-server defaults``
