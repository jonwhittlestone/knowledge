# Notes for Discourse on Docker on AWS Lightsail

Resource: https://github.com/discourse/discourse/blob/master/docs/INSTALL-cloud.md

* set up a subdomain MX record in GoDaddy DNS to get email sending to gsuite inbox at jon@forum.howapped.com

Type	Name	Value	TTL	Actions
MX	forum	ASPMX.L.GOOGLE.COM (Priority: 10)	1 Hour

* make sure DNS has SPF - https://blog.woodpecker.co/cold-email/spf-dkim/
* Hosted on VPS/Amazon Lightsail, managed by ca-tm-main
* `ssh -i ~/.ssh/jon-ca-tm-main-lightsail.pem ubuntu@54.226.32.8`
* http://forum.howapped.com/
