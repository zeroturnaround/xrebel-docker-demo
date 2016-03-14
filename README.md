#XRebel Demo

The demo is build with [Docker Compose](https://docs.docker.com/compose/). It starts 3 Docker containers with the following components:

- [Modified Petclinic application](https://github.com/zeroturnaround/xrebel-demo-petclinic) deployed to Tomcat, started with XRebel
- [Supplements application](https://github.com/zeroturnaround/xrebel-demo-supplements) deployed to Tomcat, started with XRebel
- MongoDB instance

See [docker-compose.yml](docker-compose.yml) for the components setup description. 

##Prerequisites

[Docker Toolbox](https://docs.docker.com/mac/step_one/) is required in order to run this demo.

##How to run

- Start Docker Machine - https://docs.docker.com/machine/get-started/

First, create new machine instance:
```
$ docker-machine create --driver virtualbox dev
Creating VirtualBox VM...
Creating SSH key...
Starting VirtualBox VM...
Starting VM...
To see how to connect Docker to this machine, run: docker-machine env dev
```
Check if the new machine is running:

```
$ docker-machine ls
NAME      ACTIVE   DRIVER       STATE     URL                         SWARM
default            virtualbox   Stopped
dev       *        virtualbox   Running   tcp://192.168.99.100:2376
```
Start the machine instance in case it is not running yet:

```
$ docker-machine start dev
Starting VM...
Started machines may have new IP addresses. You may need to re-run the `docker-machine env` command.

$ docker-machine env dev
export DOCKER_TLS_VERIFY="1"
export DOCKER_HOST="tcp://192.168.99.100:2376"
export DOCKER_CERT_PATH="/Users/anton/.docker/machine/machines/dev"
export DOCKER_MACHINE_NAME="dev"
# Run this command to configure your shell:
# eval "$(docker-machine env dev)"
```
As suggested, run the eval command to configure your shell:

```
$ eval "$(docker-machine env dev)"
```

- Pull this repository and start with Docker Compose
```
git clone https://bitbucket.org/zeroturnaround/xrebel-demo1
cd xrebel-demo1
docker-compose up
```

To access the newly started Petclinic application run the following command:

```
open http://$(docker-machine ip $(echo $DOCKER_MACHINE_NAME)):8000/petclinic
```
or

```
./open.sh
```


