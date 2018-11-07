# Scaling Python for Big Data - O'Reilly

- https://github.com/kjam/data-pipelines-course
- 

## Setup

* Install Anaconda / Install Jupyter Notebooks


----
### 04 - What should we automate

* How and what to automate in data pipeline

----
### 05 Server setup

* https://plusbryan.com/my-first-5-minutes-on-a-server-or-essential-security-for-linux-servers 

----
### 06 Maintenance of system

- Reliability - http://www.charleshooper.net/blog/briefly-operator-requirements/
- Linux debugging tools - https://jvns.ca/blog/2016/07/03/debugging-tools-i-love/
- Container monitoring - https://www.datadoghq.com/blog/monitor-docker-datadog/
- Load testing with Twitter Iago - https://github.com/twitter/iago

----
### 07 - What is a queue

- Abstract data structure  to hold tasks, data, message for later processing
- A distributed queue available across many machines
- Think of a line in supermarket, if queue is getting long - open more checkout lanes with more workers
- Does queue take oldest (Last In First Out), or newest (First In First Out)
- Priority is the skipping of the line/queue
- Messaging queue is a type of queuing tech: RabbitMQ, Amazon SQS, Apache Kafka.
- Mongo and Redis can also be used

----
### 08 - Producers and Consumers

- Producer creates new work (enqueue)
- Consumer - performing the work (dequeue)

- Consumers taking away from data pipeline. Eg saving to db

...

----
### 09 - Celery

- Works with scheduled, event-driven automation to turn any python function into a task
- Use it with various backends like RabbitMQ and Redis
- Brokers: http://docs.celeryproject.org/en/latest/getting-started/brokers/

- Built-in plugin support for Django

- Flower: web dashboard

----
### 10 - How to use Celery

- Celery is in charge of scaling the consumers
- Celery is in charge of managing the tasks that consumers perform
- Celery is in charge of sending data to the messaging queue

- Diagram: https://goo.gl/bwHbcx

- Install rabbitmq - `brew install rabbitmq`
- To install rabbitMQ variant of celery `pip install celery[rabbitmq]`
- set up a user and a vritualhost for the rabbitmq
- can use rabbitmq control commands `rabbitmqctl add_user celery_user p@55word`

----
### 11 - Building first task with Pandas to get stock info

- Now Celery is installed and running and rabbitmq is running
- Celery workers run with the celery application

- Define the tasks and celery config
- in tasks.py, define a function then use decorator `@app.task`
- check function works properly first in ipython repl
- celery config in `celery_app.py`
- start a worker with `celery -A tasks worker  --loglevel=INFO`

----
### 12 - Setting up distributed task queue on another server and setting up with Ansible

- Automation framework - Ansible
- Use Ansible to deploy and install python3 programs
- Install Ansible itself in a python2 environment
- Can just set up a git remote to push-pull tasks with celery installed in host


