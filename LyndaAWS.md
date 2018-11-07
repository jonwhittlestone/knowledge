# Lynda AWS Traning

https://app.plex.tv/web/app#!/server/bc0049189e861dd58c943d9c7307957a899ce527/playlist/55955

## Chapter 1 - Cloud Concepts

### 102 - Technical Benefits

- Automation
- Auto-scaling
- efficient development/testability

### 103 - Scalabale Architectures

‘Scaling Out’ - Horizontal scaling - add capacity / adding nodes / adding web servers

‘Scaling In’ - the opposite of scaling ot

‘Scaling up’ - vertical scaling - adding resources to a single node / component / increasing CPUs, memory

‘Scaling Down’ - opposite of scaling up

### 104 - Elasticity

Does away with the need for planning, time and money

Example of scaling out manually by 5 servers because of marketing activity

### 105 - Letting go of Constraints

Existing systems may not map directly to the cloud

Especially powerful when combining with the cloud’s on-demand provisioning model

Might be necessary to rethink application architecture like using other services like a distributed memory cache

Scaling out database layer by distributing across a cluster, or utilise other DB sharing techniques

### 106 - The role of Admins

Provisioning of servers and traditional tasks are just API calls

DB Admins need to use VM images for deployment

DB Admins have myriad of options open to them for scalability

There should be increased knowledge sharing between ‘admins’ and application developers

----

## Chapter 2 - High Level Cloud best-practices

Brief overview which apply to any cloud provider

### 0201 - Design for failure

Avoid single points of failure - for example - the database tier.

Use RDS to set up a failover, secondary db server. RDS takes care of all the messy synchronisation details

The failover process may involve other hardware or software processes.

### 202 - Implement Elasticity

method 1: scaling to a schedule
method 2: preemptive schedule according to an offline event
method 3: set up monitoring of certain metrics    

The build and deployment process must be automated before these 3 methods can be attempted.
This can be done with a method called ‘Bootstrapping your instances’ This is - how can app be provisioned from cold

### 203 - Loose Coupling

Design principle

Strive for a system that copes if a component fails, and can just keep on carrying on if nothing’s happened

eg. In an app, the app servers might not be aware of the db servers, and vice-versa

Achieving loose coupling then allows for easy addition and subtraction of components to match demand

Change web and app servers to be attached to a load balancer which will allow the connection to be distributed to any number of app servers

### 204 Keeping things secure

Need to know how cloud responsibilities are shared between cloud provider (AWS) and cloud user (you)

Provider: Physical, infrastructure, customer, tenancy

User: Network, Application, Protect data in motion (SSL)

SSL certs at EC2 instance or load balancer level

Protected data at rest - encrypting file system storage (local storage which will not survive an instance terminating)

Protect access credentials
* AWS access keys (public, private - when using API)
* * x509 certificates

Rather than have the private key in code, build application, build so key is passed in as arguments at runtime

IAM to manage access control

AWS provides security groups which act as your firewalls to associated instances

----

## Chapter 3 - Designing for failure in AWS

### 301 - EC2 + Elastic IPs

You’ll need some servers. EC2 servers/instances. The elastic nature means you don’t have to worry too much up-front about scalability and big vs. small & few vs. many

Elastic IPs are per account and are controlled by the cloud user until we choose to specifically release it

Traditionally, dying of a server, means repointing your DNS at another server and waiting for it to propagate.

### 302 - AWS regions and availability zones

AWS regions are independent collections of geographically separate collections of AWS resources

Can address specific regulatory and compliance requirements according to the region

EU region (located in Ireland) / South America / Asia Pacific (Singapore, Sydney, Tokyo, Beijing)

no data replication between regions

can use more than one region if you are required to have very strict HA requirements that call for redundant systems and disaster recovery

Within a region, you can have geographical isolation as availabilityaphical distribution'

Easy to manage for backups, security managemenconfigure domain name in your application

### 303 - Amazon machine image (AMI)

Packaged environment to create and boot an EC2 instance
 
 Can deploy several which correspond to components (DB server, APP server)
 
 AMI contents:
 * template for root volume
     *  OS
 *  launch permissions
    * control which AWS accounts can using the AMI
 * block device mapping
* specifies volumes to attach to the instance when it’s launched

Can have AMIs that are public

When creating an EC2 instance, must specify an AMI which is responsible

 Chapter 03 - Maintain an AMI to be able to restore and clone environments across availability zones

### 304 - Elastic Load Balancing - Use ELB to distribute across multiple zones

A service that provides a component that balances traffic across EC2 instances and AZ’s

ELB - AWS supports elasticity by default

HTTP, HTTPS and TCP

Single CNAME (to point web app domain names to) for DNS config and doesn’t change during scaling

As traffic increases AWS adds ip address to the ELB’s DNS entry

And vice-versa for decreasing traffic

### 305 - Cloud Watch- ‘Use to get visibility on hardware or software performance issues'
 
 Resource application monitoring service Assists in monitoring.
 
 Discrete metrics on CPU Utilisation, Disk I/O, Network Traffic
 
 Free / 5 minute intervals
 
### 306 - Volume Storage- ‘Use EBS and keep persistent data independent of EC2 instances'
 
 Elastic Block Storage
 
 Ephemeral Storage / Local storage
 
 Attach (multiple) EBS volumes to EC2 instances
 
 Can define provisioned IOPS
 
 Volumes up to 1TB
 
 create point-in-time snapshots, copy to other regions and S3
 
 can be viewed with cloudwatch
 
 Probably best to unmount the volume from within the instance before taking the snapshot to guarantee that you don’t have partial data (and then remount)
 
 Stored incrementally, so only the snapshots that have changed are saved.
 
 ### 0307 - Relational Database Service - ‘Use RDS to simplify security, redundancy, scalability, geographical distribution'
 
 Easy to manage for backups, security management
 
 Engine type: MySQL, Postgres, SQL server, Oracale
 
 No SSH / Root Access to these instances
 
----
### Chapter 4 - Implementing Elasticity

## 401 - Bootstrapping - 'Automate with scripts'

Creating a self-sustaining startup process that gets your app up & running on EC2

Tells instances who they are and what their role is - ‘am I an app server’ and register itself as a component in the system

Bootstrapping Tools

e.g.. Run custom scrips and tools

Chef/Puppet/Ansible

Opsworks - Free application management service (built on top of Chef)

 can access meta data with curl. e.g. hostname
 
 curl http://{ip-address}/latest/meta-data/hostsname
 
 
 to see list of possible endpoints
 
 curl http://{ip-address}/latest/meta-data/
 
 ### 402 - Auto-scaling - ’Take advantage of auto-scaling service to keep everyone happy'
 
 You define the conditions that you want to scale in or scale out
 
 Eg. If the average CPU utilisation (from cloud watch) goes above 75% for more than a minute, add two more instances
 
 Auto-scaling components
 * launch configuration: what to scale
    *  auto-scaling group: where we want to launch, define limits on num. instances to launch
    * scaling policy: how to launch, define cloud watch alarms based on certain metrics
    * scale out as well as scale in policy (to keep costs low and avoid waste
  
 ### 403 - Storage Options - ‘Take advantage of object storage options to leverage availability and scalability'
 
 * S3
 * * Objects stored in ‘buckets’
 * * not a traditional filesystem
 * * a central repository of meta-data
 * * no search
 * * stored on multiple AZs
 * * Reduced redundancy storage (RRS) option in S3 which reduces storage costs.
 * * 5TB limit on individual objects
 * * accesible via REST
 
 * eventual consistency model, so not suitable for data that changes frequently
 
 * Glacier
 
 * * good for archiving
 * * retrieval time of several hours
 
 * Cloudfront
 
 * * content delivery service for assets
 * * akamai / windows azure
 * * store on origin server
 *     * create a new cloudfront distribution
 *     * use configure domain name in your application
 * )

### 404 - Elastic Beanstalk “Conider taking Beanstalk to deploy in a fully managed cloud"

Automatically takes care of health monitoring, logging

takes care of load balancing and capacity planning

Elastic beanstalk allows you to push to git and it gives you a URL that you can access it

On a single micro EC2 instance and built from an AMI linux

Configures EC2 for auto-scaling

### 405 - Cloud Formation

Define an app stack as text template files

Condense this down to a template file and this can be used to recreate the entire landscape of AWS services

Written in JSON

can use CloudFormer

----

## Chapter 5 - Decoupling Components

### 501 - Simple Message Queue Service - 'Use SWS and the communication glue to bind components together for fail-safe, scalable and performant'

SQS allows you to pass messages between computers and app components

Rearchitect a tightly-coupled system to look like

use queue buffers, so components can communicate asynchronously


If controller B fails, controller A will still continue to perform its job and the message will buffer. If there are a lot of messages waiting by the time controller B comes back online

Example: Watermarking application. Rather than having the resizer, watermarking and notifying applications all happening in a single process, when one process is finished (eg watermarking) - it notifies the next process that it's done with a message eg ready for notification.

### 502 - SNS

notify people or applications from cloud

use pubsub protocol

subscribers to the the topics, receive the messages

Example: notify ops of an issue in production system

Raise an alarm based on an event and publish based on a topic

Can send messages in different protocols with single GET request. ie http, sms, email or an Amazon SMS queue.

SNS allows us to set up a push notification system

### 503 - Dynamo DB: A NoSQL, schema-less database

High latency, high throughput using SSDs

Automatically replicated accross multiple AZ

Helps keep app stateless because sessions can be stored in shared locations

Can use sticky session mgmt on a load balancer where LB sends user back to the same server but will introduce single point of failure. SOLUTION - store session state outside of server in centralised location


----

## Chapter 6 - Keeping Things Secure

### 601 Shared security model - understand the security model for the resources being used

Responsobility for security is shared between Amazon (provider) and user (developer)

Consumer is responsible for securing operating systems, platforms, data

Think about and implement security at every level of the app

#### Categories of Services

##### IAAS (Infrastructure)

AWS is hands-off with regard to their responsibilities

Services similar to traditional rack-server model

- EC2
- EBS
- Auto-scaling
- VPC
- Direct Connect

##### PAAS - Container Services

Amazon now takes responsobility for OS and application management that powers the platform.

- Elastic Beanstalk
- RDS
- EMR
- OpsWorks
- CloudFormation

#### SAAS - Abstracted the platform or management layer

I, the AWS consumer, consume these endpoints. The user has the least control and the least amount of securiy responsobility.

- S3
- SQS
- DynamoDB
- SNS
- SES
- CloudSearch

### 602 IAM / Identity and Access Management

Created an account = created a 'Master' account

Do not use for accesing services and resources

Should set up appropriate access control structures through IAM

Create Users, Groups, Roles and Permissions and apply to each services and API calls

Adheres to security principle; least privilege. New Users can't access shit.

Creates groups so privileges can be managed on a group level

IAM roles allow users or services to act on behalf of the master account. Can be done on a temporary basis

### 603 Security Groups

Set of rules you create that determine who can communicate with the servers that belong to that group
Virtual Firewalls, control inbound traffic

AWS will assign a default security group (restrictive)

Traffic Type: eg SSH, TCP, RDP
Protocol: eg. TCP
Port range: one or more ports that are open for the traffic type 
Source: security group or IP address

CIDR notation - Classless Internet Routing Notation -  specifying IP address and associated routing prefix by appending number of leading bits after a slash

Where an IP address is composed of 4 octets
0.0.0.0/32          no access
72.183.104.30/32    only a single IP address can access
72.183.104.0/24     first 3 octets must match
72.183.0.0/16       first 2 octets must match
.. etc ..

A bastion server is a well-known security practice for allowing good guys into the network, but keeping the bad guys out

Applying security groups diagram


### 604 Virtual Private Cloud / Take time to set up

 New way to launch EC2 instances which is logically isolated to only one AWS account and nodes are not all public addressable on the public internet as was once the case.

 Can specify own IP range and architect range into public and/or private sub-nets

Control both inbound and outbound traffic

Can also connect [VPC](VPC) to onsite system that aren't hosten on AWS with VPN

Setting up - takes a little time and thought
    * Set region and AZ
    * come up with block of IPs
    * create subnets (inside one AZ)
    * Attach gateway interfaces to allow access to your network / it's now a public subnet


----
## Chapter 7 - Theory into Practice

### intro / Systems Architecture diagram

Auto-scaling to ensure we never have less than two web servers running

High Availability by having a server in Zone A and one in Zone B

Enter via Load Balancer on port 80

### 702 Signup

u: dev@howapped.com

### 703 Set up new IAM user

Signin Link: https://114085210620.signin.aws.amazon.com/console

So we don't use AWS as the account owner which has access to all the billing info

Everyone who needs access, should have their own user profile

** SECTION > IAM
    ** USERS
        ** Add User
        ** Give user priveliges by Attaching a AdministratorAccess Policy 
        
 A policy lets us define actions
 
In JSON view unless explicityly defined, actions and resources are all denied. Can add individual actions or resources

### 0704 Generating a key pair

** EC2
    ** Key Pairs
        ** Create key pair
            - good practice to rotate and to create one for dev and one for prod
            - howapped_jon_prod.pem is your private key
            - specify readonly for owner permission `chmod 0400 ~/Downloads/howapped_jon_prod.pem`

### 0705 Set up security groups

Set up 3 security groups / part of the EC2 service in the console

** EC2 Dashboard
    ** Security Groups
        ' Amazon already set us up with a default security group with no permissions
        
        ** Create security group for Load Balancer
            ' with corresponding rules 
            
            ** Create
            
Do the same for the web tier

### 0706 ELB

** EC2
    ** Load Balancer
        ** Create Load Balancer
            **  name = web-tier-elb
                don't create internal load balancer
                set load balancer port ==> instance port
                can manage SSL certificates just on LB
            **  health check / LB will only route traffic to healthy instances
                ping path with heartbeat.php
            **  assign security groups
                which we've already set up
            **  add instances to load balancer
                add instances soon
                cross-zone load balancing ✔
            **  Review and create

  ### 0707 Launching an EC2 instance
  
  ** EC2
    ** Instances
        ** Launch Instance
            ** Choose AMI
                ** Amazon AMI Linux Image
                ** Choose instance size for your app
                    ** Configure Instance Details
                        ** Advanced Details
                            ** User Data
                                - use cloud init to set configuration needed for a LAMP stack server
                ** Add storage
                ** Tag instance
                ** Choose security group
                ** Launch Instance
                ** Specify key pair
  
### 0708 Accessing the newly created server through http
 
 Make sure status checks have passed / are green
 Get public IP address
 In order to check that user data worked and Apache was installed, add a new security group rule temporarily to allow inbound traffic on port 80 to hit the instance
  
### 0709 Add health-check so we can put it behind a load balancer

Add a rule as before, to allow us to SSH into this box

`ssh -i ~/.ssh/howapped_jon_prod.pem <public_ip_of_web_server> -l ec2-user`

Add hearbeat to docroot that we need for load balancer to understand if instance is healthy

10m.18s Permission changes to document root / change ownership

Any members of the www-data group will be able to add/modify files to the web server
            
Add user to the group, and also change ownership of the files to www group

Set the write permissions and group id ownership on all future subdirectories

    [ec2-user@ip-172-31-26-234 ~]$ sudo chown -R root:www /var/www
    [ec2-user@ip-172-31-26-234 ~]$ sudo chmod 2775 /var/www
    [ec2-user@ip-172-31-26-234 ~]$ find /var/www -type d -exec sudo chmod 2775 {} +
    [ec2-user@ip-172-31-26-234 ~]$ find /var/www -type f -exec sudo chmod 0664 {} +

add `heartbeat.php`

add `instance.php` to get instance identifier which gets contents of meta data from endpoint

Have everything in place to add instance to the load balancer

    ** Load Balancers
        ** Edit Instances
            ** Add
            Status will be `OutOfService` / Takes a bit of time to register
            Go to DNS name in browser and will be directed to Load Balancer! / Will get default Apache test page

Check ELB-HealthChecker is working by tailing Apache logs on instance

### 0710 - Add RDS instance for persistent DB tier

** RDS
    ** Instances
        ** Create New
            ** Mysql
                ** Production purposes?
                Multi-AZ deployment, Amazon takes care of syncing and fail-over
                ** Specify DB Details
                DB instance class = choose smallest
                Allocated Storage = 5 gb
                No provisioned IOPS
            ** Set Advanced settings - Security Group ( Web Tier )
            ** Launch
 
 Test to see if we can connect to it from web tier
 
 ### 0711 - Create an AMI from the instance we have set up
 
 Save an image so we can quickly create clones of environment
 
 ** EC2
    ** Instances
        ** Right Click - Instance Management
            ** Create Image
 
 Create an image of the web server "initial dev image"
 
 Spin up a new instance in a different Availability zone
 
 ** AMIs
    ** Right click - Launch
        ** Configure instance details
        Network = vpc
        Subnet = 1a
        ** Add storage
        ** Choose existing security group
        ** Review and Launch
 
 Add it behind Load balancer
 
 ### 0712 - Set up Auto-scaling / automatically spin up new servers in an automated fashion
 
 New servers spin up automatically
 
 *WHAT* to scale - Launch configuration
 
 *HOW* to scale - Auto-scaling group
    scaling in or out with policies
    
 Web server tier is never allowed to have less than 2 web servers up and running
 
 ** EC2
    ** Auto Scaling
       ** Launch Configuration
            ** Create Auto Scaling group
                - choose existing AMI
                - name=web-server-launch-config 
                - security group = web-tier
                - group size = start with 2 instances
                - choose both subnets ( A and B )
                - Advanced Details: ✔ Receive traffic from Elastic Load Balancer
                - Health check type: ELB (hearbeat.php that we set up on the ELB)
                - Add notification if you had SNS topic set up, get a notification any time scaling event happens
  
  Manufacture a disaster by shutting down a web server
  
  Auto-scaling group takes care of spinning up a new instance / Look at history of auto-scaling group to see this has happened
  
----
## Chapter 8 - Integrating our application with other AWS Services

### 801 SDK

Launching an instance in a specific role
    - create the IAM role
    - define which accounts/services can assume the role
    - define which API actions/resources the app can use
    - specify the roles when you launch your instances
 
 ** IAM
    ** Roles
        ** Create new Role
            - Role name: webserver
            - Administrator role

Then launch an instance with that role

** AMI
    ** Launch image
        ** Choose instance: micro image
            ** Configure Instance Details
                - IAM role: webserver
 
 SSH in to get credentials needed for accessing over the API
    [ec2-user@ip-172-31-33-253 ~]$ curl http://169.254.169.254/latest/meta-data/iam/security-credentials/webserver
    
### 802 Installing the PHP SDK

Install on the instance
change directories to where app resides (/var/www/html)
in composer.json - add deps

### 803 - Writing a quick php script to interface with AWS services using the SDK

Use the SDK to interface with S3 storage

`createbucket.php` does not contain explicit credentials to use the SDK but since the instance has been launched in the role and the sdk is set up to obtain the credentials from the instance meta-data, they don't need to be provided. done automatically, no hard-coding needed etc.

There are alternative ways to pass in security credentials if needed


----

## 09 Conclusion

"
