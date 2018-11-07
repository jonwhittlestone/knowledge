#ECR / Amazon EC2 Container Service

Steps to set up EB-UAT

Login to wonderinc profile on AWS-CLI and use the docker registry

1. ▶ ~/code/ivxs/terraform/bin/mfa-login.sh jon
2. ▶ ~/code/ivxs/terraform/bin/assume-client-admin.sh wonderinc
3. ▶ aws ecr get-login --profile ca-tm-wonderinc-assumed --region eu-west-1
4. And then run what you get back

    view all images in particular repository            aws ecr list-images --repository gatekeeper --profile ca-tm-wonderinc-assumed --region eu-west-1
    ssh into ca_tm > bastion                            ssh -i ~/.ssh/ca_tm.pem -A jon@ec2-34-250-56-242.eu-west-1.compute.amazonaws.com









