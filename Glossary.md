# AWS Glosary

#### Elasticache
A distributed memory cache. Based on memchached

#### IOPS
Input/Output operations per second (database)

#### RDS
Amazon’s relational database service

#### Console UI
A place to handle automation where no scripting is required

#### Bootstrapping instances
Create a self-sustaining startup process to get your app running on an EC2 instance

#### Load Balancer
Allows the connection to be distributed to another loosely coupled components

#### x509 Certificate

#### IAM
AWS service to create users and manage their permissions by assigning them roles and placing them into groups

#### EC2 Instances
Elastic cloud compute which are the servers in the cloud

#### Elastic IPs
Static IPs designed for cloud computing is created in account and not specific to a particular instance

#### AWS regions
Geographically independent regions each of which is its own collection of resources. 4 regions in North America, one in the EU etc.
Each region consists of Availability zones

#### Availability Zone
Isolated distinct locations that are isolated. Think of them as data centres
Linked to each other via fibre

#### AMI - Amazon Machine Image
Packaged environment and settings that is the basic unit of deployment to create and boot an EC2 instance

Part of the EC2 service in Management console

#### AWS Management console
Log in in the browser, See all of the AWS services available

#### Fault tolerance
This is achieved by Elastic Load Balancing

#### ELB
Elastic Load Balancer - component that balances traffic load over multiple EC2 instances and AZ, scales to meet traffic demands

#### Cloudwatch
Performance application monitoring and system utilisation metrics

#### EBS / Elastic Block Storage
Storage that persists after an instance is terminated

#### Ephemeral / Local Storage
Storage that doesn’t survive termination

#### Provisioned IOPS
When creating volumes, specific performance parameters can be specified

#### RDS
Relational Database Service - setup, scale relation database in the cloud

#### Cloud-init
Linux tool to specify scripts or shell commands / address server bootstrap needs, will be automatically run during the startup instance lifecycle.

#### Glacier
?

#### Cloudfront
Content caching CDN

#### Storage Gateway
Sync. on-prem storage with cloud-based storage

#### Scaling policy
Define the conditions in which we should scale in and scale out according to traffic levels or CPU utilisation metrics from Cloudwatch

#### Dynamo DB
Amazon’s NoSQL database option / Automatically replicated across AZs

#### S3
Object store

#### RRS
Reduced redundancy storage option in S3 which reduces storage costs

#### Elastic Beanstalk
PaaS takes care of load balancing and capacity planning, monitoring and logging and auto-scaling rules

#### Cloud Formation Template
Allows the user to condense the description of a full AWS services stack down to a document to recreate or share with others

#### SQS / Simple Message Queue Service
Implementation of message queuing software in cloud. A pull notification system that requires applications to poll for new messages

#### SNS
Simple notification service / notify people or applications from the cloud / push notification system with SMS, Email, Amazone SMS queue name etc

#### EMR [](/)

#### [Policy](Policy) / Security policy
Attach these sets of permissions to IAM users. A policy describes one or more statements, each of which describe one set of permissions / let us define actions that will be allowed (depending on `Effect`)


### CIDR notation
A notation to specify list of allowed IP addresses and which octets are permitted

