# Making It Easier with Docker Compose: The Multi-Container Tool

* Why : Configure relationships between containers &
Save our docker container to run the settings in easy to read file & create one liner developer environment startups. 
* Comprised of 2 seperated but related things.
* YAML formatted file that describes our solutions for: 
Containers, Networks and Volumes.
* A CLI tool docker-compose used for local dev/test automation with those YAML files.

## Docker Compose and The Docker-compose.yml File
```
docker-compose.yml

https://docs.docker.com
```

## Trying Out Basic Compose Commands
* CLI tools comes with Docker for linux but seperate to download linux.
* Not a production-grade tool but ideal for local development and test.
* <b>Two common commands are: </b>
     * docker-compose up : to setup volumes/networks and start all containers.
     * docker-compose down : to stop all containers and remove cont/vol/net.
* If all your projects had a Dockerfile and docker-compose.yml file then new devloper onboarding would be: 
  * git clone github.com/some/software
  * docker-compose up


```
pcat docker-compose.yml

Or,

cat docker-compose.yml

docker-compose up

Check in : http://localhost:81/

docker-compose up -d

docker-compose logs

docker-compose --help

docker-compose ps

docker-compose top

docker-compose down
```

## Assignment Answers: Build a Compose File for a Multi-Container Service
```
docker-compose.yml

docker pull drupal

docker image inspect drupal

docker-compose up

https://hub.docker.com

docker-compose down --help

docker-compose down -v
```

## Adding Image Building to Compose Files
```
docker-compose.yml

docker-compose up

docker-compose up --build

docker-compose down

docker image ls

docker-compose down --help

docker image rm nginx-custom

docker image ls

docker-compose up -d

docker image ls

docker-compose down --help

docker-compose down --rmi local
```

## Assignment Answers: Compose for Run-Time Image Building and Multi-Container Dev
```
docker-compose up

docker-compose down

docker-compose up
```

* Which is the minimum recommended version for a docker-compose.yml file?
ANSWER: 2
* Which of the following does "docker-compose up" automatically create, even if not manually specified in the compose file?
ANSWER: Network
* What is the 'build context' in a compose file supposed to do?
ANSWER: It is meant to specify where the Dockerfile of the image is supported to build from. 

* The "ports:" key in a compose file does the same thing as the EXPOSE stanza in a Dockerfile.

ANSWER: False

* Usernames for a database, when placed in a compose file of a specific service, would best fit placed under which of the following keys?

ANSWER: environment:

* Where does compose derive a DNS name from?

ANSWER: service names


### Learning resources
* https://yaml.org/start.html
* https://yaml.org/refcard.html
* https://docs.docker.com/compose/compose-file/compose-versioning/
* https://github.com/docker/compose/releases
* https://github.com/docker/compose/releases
* https://github.com/BretFisher/ama/issues/8
* https://docs.docker.com/compose/compose-file/#links
* https://docs.docker.com/compose/compose-file/
* https://docs.docker.com/compose/compose-file/#build
