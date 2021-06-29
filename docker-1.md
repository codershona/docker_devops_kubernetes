## Creating and Using Docker Containers 

### Getting Started

* Install Nginx to run docker in web server.

* Docker Installation and Configuration :
```
docker version

docker info

docker

docker container run

docker run
```
* Install Mongo on your linux environment.
* Install MySql on your linux environment.
* Install Docker CE, docker compose and docker machine in linux environment.
* Managing Multiple Containers.


  Run this commands on your terminal :
```
docker container run -d -p 3306:3306 --name db -e MYSQL_RANDOM_ROOT_PASSWORD=yes mysql
```
```
docker container logs db
```
Here You can add any name in the place where I had added webserver and -d actually detach port and -p means the port.
```
docker container run -d --name webserver -p 8080:80 httpd
```
For example :
```
docker container run -d --name webserver1 -p 8080:80 httpd
```
```
docker ps
```
Here You can add any name in the place where I had added proxy. 
```
docker container run -d --name proxy -p 80:80 nginx
```
For example : 
```
docker container run -d --name proxy1 -p 80:80 nginx
```

```
docker ps
```
```
docker container ls
```
```
docker container stop TAB COMPLETION
```
```
docker ps -a
```
```
docker container ls -a
```
```
docker container rm
```
```
docker ps -a
```
```
docker image ls
```

If you wanted to view running containers as well as containers that you have stopped and not removed, what command would we can use,
```
docker container ls -a or, docker ps -a
```

The -d flag can able to run command in a docker, it detaches the container to run in the background and returns you to the shell prompt. It's the short version of --detach. By running in detached mode, we are able to have access to our command line when the container spins up and runs. Without it, we would have logs constantly fed onto the screen.

Can the following two commands could create a port conflict error with each other?
docker container run -p 80:80 -d nginx
docker container run -p 8080:80 -d nginx

Reply : No 

If I ran 'docker container run -p 80:80 nginx' and my command line is gone and everything looks frozen. Whyat is the reason?

Because you did not specify the -d flag to detach in the background and there are not any Nginx logs yet. You didn't specify the -d flag to detach it in the background, and there aren't any logs coming across the screen because you haven't connected to the published port yet, so Nginx has nothing to log about.

## Starting a Nginx Web Server :

```
docker container run --publish 80:80 nginx

docker container run --publish 80:80 --detach nginx

docker container ls

docker container stop 690

docker container ls

docker container ls -a

docker container run --publish 80:80 --detach --name webhost nginx

docker container ls -a

docker container logs webhost

docker container top

docker container top webhost

docker container --help

docker container ls -a

docker container rm 63f 690 ode

docker container ls

docker container rm -f 63f

docker container ls -a
```

## Container VS. VM: This is another Process :
```
docker run --name mongo -d mongo

docker ps

docker top mongo

docker stop mongo

docker ps

docker top mongo

docker start mongo

docker ps

docker top mongo
```

## Check the current process in Containers: CLI Process Monitoring :
 
 * docker container top is used to process list in one conatiner.
 * docker container inspect isused to see the details of the one container config.
 * docker container stats is used to check the performance of the stats for all containers.

```
docker container run -d --name nginx nginx

docker container run -d --name mysql -e MYSQL_RANDOM_ROOT_PASSWORD=true mysql

docker container ls

docker container top mysql

docker container top nginx

docker container inspect mysql

docker container stats --help

docker container stats

docker container ls
```


## Shell Inside Containers: No Need for SSH

 * docker container run -it is used to start new container interactively.
 * docker container exec -it used to run additional command in exisiting container. 
 * No SSH needed because Docker Cli is a great substitute for adding SSh to Containers.
 * docker container exec used to run additional process in running container.
 * Alphine Linux is a small security focused distribution.
 * Using diffrent Linux distros such as, ubuntu and alpine in container.

```
docker container run -help

docker container run -it --name proxy nginx bash

docker container ls

docker container ls -a

docker container run -it --name ubuntu ubuntu

docker container ls

docker container ls -a

docker container start --help

docker container start -ai ubuntu

docker container exec --help

docker container exec -it mysql bash

docker container ls

docker pull alpine

docker image ls

docker container run -it alpine bash

docker container run -it alpine sh
```

## Docker Networks: Concepts for Private and Public Comms in Containers :

* Review of docker container run -p which runs that exposes the port in our local machine.
* To quick check the port - docker container port <container>.
* Each container connected to a private virtual network "bridge".
* For local dev/testing , networks usually "just work".

```
docker container run -p 80:80 --name webhost -d nginx

docker container port webhost

docker container inspect --format '{{ .NetworkSettings.IPAddress }}' webhost
```

## Docker Networks: CLI Management of Virtual Networks

* docker network ls command is actually used to show the networks.
* docker network inspect is used for to inspect a network.
* docker network create --driver is used to create a network. 
* docker network connect is used to attach a network to container.
* docker network disconnect is used to detach a network from container.


```
docker network ls

docker network inspect bridge

docker network ls

docker network create my_app_net

docker network ls

docker network create --help

docker container run -d --name new_nginx --network my_app_net nginx

docker network inspect my_app_net

docker network --help

docker network connect

docker container inspect TAB COMPLETION

docker container disconnect TAB COMPLETION

docker container inspect
```

## Docker Networks: DNS and How Containers Find Each Other :

* --link is used to enable DNS on default bridge network.
* Working process of defualt with custom networks.
* Containers will not rely on IP's for inter-communication.

```
docker container ls

docker network inspect TAB COMPLETION

docker container run -d --name my_nginx --network my_app_net nginx

docker container inspect TAB COMPLETION

docker container exec -it my_nginx ping new_nginx

docker container exec -it new_nginx ping my_nginx

docker network ls

docker container create --help
```
## CLI-App TESTING:
### Using Containers for CLI Testing :
* docker container --rm is used where we can save the cleanup.

```
docker container run --rm -it centos:7 bash

docker ps -a

docker container run --rm -it ubuntu:14.04 bash

docker ps -a
```
## DNS RR TEST : 
### DNS Round Robin Testing :

```
docker network create dude

docker container run -d --net dude --net-alias search elasticsearch:2

docker container ls

docker container run --rm --net dude alpine nslookup search

docker container run --rm --net dude centos curl -s search:9200

docker container ls

docker container rm -f TAB COMPLETION
```


