# 12 Factor Apps #


## 1. Automate from a development perspective ##

- use version control
- Allow for many deploys with CI/CD pipeline


## 2. Portable across execution environments ##


- Per-app dependencies can be brought in with a packager like `pip` or the `Gemfile`
- An app shouldn't rely on external system deps like `curl`

## 3. Config is stored in the environment ##


- Config  (`.env` for _dotenv_) for operating environment in a `Dockerfile` or collection of services in `docker-compose.yml`. Can be grouped according to environments eg. developmnent, test and production
- Config for CI/CD should be stored in environment to denote the running of tests, deployment instructions etc.

## 4. Treat backing services as attached resources  ##

- datastores or messaginging/queing systems should not be treated separately. There should be no distinction in the code.
- Different versions of say, a 3rd-Party SMTP service can be swapped with another quickly, and easily.

## 5. Build, release, run  ##

- separate build and run stages
- Builds are initiated by developers
- A run stage should be kept to as few moving parts as possible
- a release should typically be made with a symlink to a newly deployed directory with the ability to rollback


## 6.  Processes ##

- Apps should be stateless and not operatore sticky sessions.
- Session data can be stored in Redis with time-expiration


## 7.  Port binding  ##

- Services are exposed by a specific port
- Should not rely on runtime injection of a web server, and should be self-contained
- It's the job of the web app to export HTTP as a service by bind to a port and listening to requests


## 8.  Concurrency - horizontally scaling  ##
- The ability to horizontally scale on multiple physical machines
- Rely on the operating system's process manager
- Developer can architect their app to handle diverse worklads. Eg. HTTP requests handled by a web process and long-running background tasks handled by a worker process


## 9.  Disposability - speed of startup  ##

- a startup process shjould only take a few seconds
- shutdown happens when the receive a SIGTERM signal from the process manager

## 10.  Dev/prod partity  ##

- keep development, staging and production as similar as possible

## 11.  Logs  ##

- Inspecting an apps behaviour over time
- Treat logs as event streams.
- Centralised on cloud eg. AWS Cloudwatch

## 12.  Admin Processes  ##
- One off tasks from command line
    - eg `manage.py migrate` for Django, `rake db.migrate` for Rails 
- One-off process shipped run against the release
- Admin code is shipped with the application code
