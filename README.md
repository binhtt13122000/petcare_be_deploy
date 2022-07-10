## Part 1 - Preparation
These steps describe an PetCare Backend installation on e.g. a DigitalOcean Droplet. 

>Note: To interact from your windows machine with the droplet use putty.

### Droplet 
Digital Ocean Droplet, 1 CPU, 2 GB, 50 GB SSD  
OS, Ubuntu 20.04 (LTS) x64

### Access via ssh
ssh root@ip-of-the-host
## Part 2 - Install docker and docker-compose

### Install Docker
The following steps are required to install Docker on the Droplet. Reference: https://docs.docker.com/engine/install/ubuntu/

```bash
# set up the repository
apt install \
  apt-transport-https \
  ca-certificates \
  curl \
  gnupg-agent \
  software-properties-common

# add Docker’s official GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# set up the stable repository
add-apt-repository \
  "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) \
  stable"

# install docker engine
apt update
apt install docker-ce docker-ce-cli containerd.io

# check the docker version
docker --version
```

### Install Docker-Compose
The following steps are required to install docker-compose on the Droplet. Reference: https://docs.docker.com/compose/install/

```bash
# install docker-compose
curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

# apply executable permissions to the binary
chmod +x /usr/local/bin/docker-compose

# check the docker-compose version
docker-compose --version
```
## Part 3 - Basic Guide
### Pull this git repository
```bash
$ git pull origin https://github.com/binhtt13122000/petcare_be_deploy.git
``` 
After that, you must change certbot's command: Replace email and hostname
#### Run script to create ssl certificate
```bash
$ pwd //print working directory
> /working_directory
$ mkdir dhparam
$ cd dhparam
$ openssl dhparam -out /working_directory/dhparam-2048.pem 2048
$ ls
> dhparam-2048.pem
```
#### Run docker-compose 
```bash
$ docker-compose up -d
```
#### Check
```bash
$ docker ps -a
```