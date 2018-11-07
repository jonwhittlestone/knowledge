# Ansible From Udemy #
    /Users/jon/code/playground/DEVOPS/Ansible/udemy

Using Mac as an Ansible controller
    pip install --upgrade ansibleo
    
Simple Pythong flask app, served by apache and mod_wsgi behind
nginx load balancer

----
## Preparation ##

### 07 Appendix ###

* 052 Authentication with SSH keys

generate a keypair with ssh-keygen

add it to ~/.ssh/authorized_keys

ssh with it using
    ssh -i /path/to/file machinealias
    
* 053 YAML
YAML hates tabs / needs to be spaces
----
### Foundation ###

* 005 Inventory pt1

* 006 Inventory pt2 
 
* 007 Hosts selection

select a subset of your inventory
    ▶ ansible --list-hosts "loadbalancer"

* 008 Tasks
    ▶ ansible -m command -a "hostname" all

* 009 Plays
Playbook is a YAML file made up of plays 
A play is a set of target hosts
A playbook runs multiple tasks in succession

* 010 - Playbook execution
    $ ansible-playbook playbooks/hostname.yml

----
### 03 Playbooks ###

* 011 - Playbooks Introduction
4 pillars of a linux application
    1. packages needed to run app (yum, apt etc)
    2. service handler - upstart, systemd, supervisor - to track service
    3. overall system configuration (iptables, firewalls rules)
    4. config file for the app itself
 
* 012/052 - Packages apt
create a playbook for each of our roles to install packages
    ---
    - hosts: loadbalancer
    -   become: true
    -   tasks:
        -     - name: install nginx
        -       apt: name=nginx state=present update_cache=yes

`present` param looks to see if package is is installed, on initial install

create a new file for database tier `database.yml`

* 013/052 - packages_become / using sudo
Executing playbooks for the roles
    ansible-playbook loadbalancer.yml
    
We need to tell Ansible to invoke super user privelege with `become: true`

* 014/052 - packages_with_items

with_items and then interpolate/inject with jinja
    ---
    - hosts: webserver
    -   become: true
    -   tasks:
        -     - name: install web components
        -       apt: name={{item}} state=present update_cache=yes
        -       with_items:
            -         - apache2
            -         - libapache2-mod-wsgi
            -         - python-pip
            -         - python-virtualenv
            -         - python-mysqldb
            
* 015/052 - the service module

the services are running, we just need to tell Ansible about
    service: name=apache2 state=started enabled=yes

Install curl on control machine, create control.yml

* 016/052 - stack restart / support playbook

how to get the stack to an initial state that i can trust
    stack_restart.yml
    
* 017/052 Services, apache2 handlers, notify
- enabling `libapache2-mod-wsgi`
    - create a new task
        - 'ensure mod_wsgi enabled'
        - using Ansible module
 
- service handler is a special type of task
    - use keyword 'notify' to ensure that the handler gets triggered
    - if there's a change in the task to enable mod_wsgi
    - if there's no change, we won't restart apache2
    - can trigger multiple notifys

* 018/052 Files
copy module - copies contents from control machine to an end host
http://docs.ansible.com/ansible/latest/modules/copy_module.html#copy

* 019/052 - application modules / pip
- in `webserver.yml` create new task to set up virtualenv
    - use ansible pip module
        - https://docs.ansible.com/ansible/2.4/pip_module.html#examples

* 020/052 - File file module
- use file module to handle to apache enable site symlinks
    - add task to disable default apache site
    - activate demo apache site
        - `- name: activate demo apache site`

nginx is stil responding with default site

* 021/052 - point nginx load balancer at webserver backend
- Use `template` file module
    - in nginx jinja template, use loop to create `upstream` for all webservers we have
    - afterwards, set up handler to restart nginx with `notify`

* 022/052 - database connection
- create the db name, user, password
- check all the ports are listening on db server
    - login to db
    - `sudo netstat -an`
        - we are only listening to 3306 on localhost, so the connection from application to db host is going to fail
            - set in /etc/mysql/my.conf
                - `bind-address`
                    - use ansible module `lineinfile` which allows preserve file in file system
        - test with `curl app01/db`

* 023/052 - mysql dependencies
- install mysql module for python `python-mysqldb`
- use ansible database modules - http://docs.ansible.com/ansible/devel/modules/list_of_database_modules.html#mysql

* 024/052 - Support playbook pt2
`stack_status.yml`
    - use `command` module not `service` as we don't want to affect/read-only for use in production
    - use `wait_for` to check that port is listening. Add param of timeout=1 to override default of 300 seconds
        - http://docs.ansible.com/ansible/latest/modules/wait_for_module.html#examples
 
 * 025/052 - Support playbook pt2 - uri register / fail
Are we getting the content back from sites
uri task for an e2e test
    http://docs.ansible.com/ansible/latest/modules/uri_module.html
    
install python dependecy httplib§
save the content using `register` module to be verified in the later `fail`` `task
        - name: verify end-to-end db response
          uri: url=http://{{item}}/db return_content=yes
          with_items: groups.loadbalancer
          register: lb_db
     
        - fail: msg="db failed to return content"
          when: "'Database Connected from' not in item.content"
          with_items: "{{lb_db.results}}"
          

 * 026/052 - Playbook summary
 
 basic configuration for infrastructure as code
how to achieve; make it work, make it right, make it fast (-- Kent Beck)
Just achieved so far - make it work
Next 'make it right' so things aren't hardcoded and more robust to gain confidence in infrastruture
 ----
### 04 Modular Configuration with Roles  ###

* 027/052 - Roles overview
Roles prevent code duplication by allowing us to specify what a resource looks like and then instantiating it when we need it

Then compose servers as a combination of various roles

Even if only one app, good idea to use roles for benefits of encapsulation

Ansible galaxy is a public repository for roles

    ansible-galaxy control init     # creates skeleton/scaffold for role

* 028/052 - converting to roles/tasks
replace tasks list with role inclusion
    ansible-playbook control.yml
    
migrate the tasks to the role

* 029/052 - Load Balancer/webserver requires files
    mkdir roles/nginx/templates
    
file locations are relative

* 030/052 - playbook that contains other playbooks
    site.yml
 use key `include`
 
 * 031/052 - variables/facts
replace hardcoded variables with values we can override

 

### 05 Advanced Execution  ###

### 06 Troubleshooting, testing and validation ###

### 07 Appendix ###
