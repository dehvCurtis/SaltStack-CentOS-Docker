# SaltStack-Docker-Dev-Env
Docker Compose setup to spin up a salt master and minions.

# Quick Start Guide

*Install Docker and Docker-Compose*

Clone repo:

`$ git clone https://github.com/dehvCurtis/SaltStack-Docker-Dev-Env`

`$ cd SaltStack-Docker-Dev-Env`

Startup both Master and Minion:

`$ docker-compose up`

  #This window will display debugging output from the salt master and minions

Open new terminal window and ensure you are in SaltStack-Docker-Dev-Env/

Login to your Master:

`$ docker-compose exec salt-master bash`

or use

`$ chmod +x master-login.sh`

`$ ./master-login.sh`

Login to your Minion:

`$ docker-compose exec salt-minion bash`

or use

`$ chmod +x minion-login.sh`

`$ ./minion-login.sh`

Now test with a ping from your Master:

`$ salt '*' test.ping`

  #The salt-master is set up to accept all minions that try to connect. Only minions within the docker-compose service network will be able to connect.

# Running Multiple Minions:

`$ docker-compose up --scale salt-minion=2`

  #If you are running more than one minion with `--scale=2`, you will need to use `docker-saltstack_salt-minion_1` and `docker-saltstack_salt-minion_2` for the minions if you want to target them individually.

# Host Names
The **hostnames** match the names of the containers - so the master is `salt-master` and the minion is `salt-minion`.
