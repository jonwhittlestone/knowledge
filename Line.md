[#](#) Bash and Command Line

* [SSH](SSH)
* [grep](grep)
* [bash](bash.md)


Kill whatever is using port 8000

    sudo lsof -t -i tcp:8000 | sudo xargs kill -9
    
Find a file on the file system, and supress the permission denied message
    find / -name expect 2>/dev/null
