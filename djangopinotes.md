# Django with Postgres, Nginx, and Gunicorn on Raspberry Pi

Resources: https://www.digitalocean.com/community/tutorials/how-to-set-up-django-with-postgres-nginx-and-gunicorn-on-ubuntu-14-04

### What works

Django dev server 
    (venv) pi@rodriguez:~/code/playground/django-gunicorn-test/src (jons-dotfiles-repo)*$ ./manage.py runserver 0.0.0.0:8000
    
Serving with gunicorn from command line
    (venv) pi@rodriguez:~/code/playground/django-gunicorn-test/src (jons-dotfiles-repo)*$ gunicorn --bind 0.0.0.0:8000 src.wsgi:application
    [2017-04-15 06:05:26 +0000] [11336] [INFO] Starting gunicorn 19.7.1
    

### Debugging

Getting 502 Nginx error so inspect `error.log`

    sudo cat /var/log/nginx/error.log
    
    
### Solution

Changed file permissions, restarted service with
    
    (venv) pi@rodriguez:/etc/nginx/sites-available $ sudo systemctl start gunicorn.service
