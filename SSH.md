# SSH

Refresh SSH entry in `~/.ssh/known_hosts` for when IP has changed

    ssh-keygen -R "cc-qa.complyadvantage.com"

----
SSH Tunnelling from localhost to an ECS cluster (To avoid a hop from Bastion)

1. Open an SSH session to the Bastion server.
    `ssh -D 127.0.0.1:8022 jon@54.77.91.77`
2. SSH to the ECS cluster
    `ssh -o ProxyCommand="nc -X 5 -x localhost:8022 %h %p" -i ~/.ssh/id_rsa jon@10.30.21.116`
3. Automate with alias in ~/.zshrc / aliases.sh

----
Get into remote postgres (eg RDS) by SSH tunnelling to bastion
1. Tunnel from host to bastion, forwarding to port 5432
    $ ssh -L 8822:db-hostname-.eu-west-1.rds.amazonaws.com:5432 jon@{bastion-ip}
2. On host, connect to localhost datbase, on port 8822

