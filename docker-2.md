# Docker Container Images:
### How can we find them and how to build it?

 * This is all about the images by building blocks of the container.
 * Think about how to find good images and in the whole process and how to manage those images.
 * TRy to manage the local image Cache when we download those images and created them on our own machines.
 * It is an app binaries and binaries which is for our app that we are working on and we need to know the way it run in th metadata.
 * Defintion: An image is an ordered collection of the root of filesystems changes and the corresponding execution parameters for uses including a container runtimes. 
 * Inside this image there is actually no complete OS, It does not have kernel and kernel modules such as, drives.
 * Smalll as one file in our built app as binary such as, golang static binary.
 * It is big as a Ubuntu distro with apt, and Apache, PHP as well as more installation. 

Also we can read this link:
```
https://github.com/moby/moby/blob/master/image/spec/v1.md
Or,
https://github.com/docker-library/official-images/tree/master/library
Or,
https://docs.docker.com/storage/storagedriver/
Or,
https://docs.docker.com/engine/reference/builder/
```

## Using Docker Hub Registry Images :
* The fundamentals of Docker Hub
* We can search in docker official or in other good public images.
* We can download images and basics of the image tags.
* We can use Alphine image or other iages options.
* Sign up or i  in docker hub: https://tinyurl.com/f9fnyamd
* Docker Hub has its apt package system for containers.
* Docker official images as well as uses of them.
* HOw to discern good public images.
* Uses of different base images such as, debian or alphine. 
```
http://hub.docker.com

docker image ls

docker pull nginx

docker pull nginx:1.11.9

docker pull nginx:1.11

docker pull nginx:1.11.9-alpine

docker image ls
```
### Images and Their Layers: Discover the Image Cache

  * Here, we can check images and its layers.
  * Image Layers
  * Union filesystems
  * History and inspects Commands
  * Copy on write
  * Image Container Layers ---> Apache ----> Container 2 ---> COW 
  * docker inspect commads actually use for the return of te JSON metadata about the image.
  * File systems changes and metadata were made by the images.
  * Each container layers were uncommon and unique to identify as well as we can stored them in once in a host. 
  * This could save the storage spaces on host or transfer time on pull or push.
  * A container were just for the single read or write layers on the top of the images.
```
docker image ls

docker history nginx:latest (old way)

docker history mysql

docker image inspect nginx
```
## Image Tagging and Pushing to Docker Hub :

 * Here , we need to unsderstand how are the container images works and fundamentals of the image layers.
 * Know all about the image tags.
 * How to upload docker hub.
 * Image ID vs. Tag.
 * Properly tagging images
 * Tagging Images for upload to Docker Hub
 * Tagging Images for upload to Docker Hub
 * How tagging is related to image ID
 * The latest tag.
 * Logging into docker hub from docker cli.
 * How to create a private docker hub images.

```
docker image tag -- help

docker image ls

docker pull mysql/mysql-server

docker image ls

docker pull nginx:mainline

docker image ls

docker image tag nginx codersh/nginx

docker image tag --help

docker image ls

docker image push codersh/nginx

docker --help

docker login

cat .docker/config.json

docker image push codersh/nginx

docker image tag codersh/nginx bretfisher/nginx:testing

docker image push codersh/nginx:testing

docker image push codersh/nginx codersh/nginx:testing

docker image ls

docker image push codersh/nginx:testing

docker image ls
```
## Building Images Using The Dockerfile Basics :


```
cd dockerfile-sample-1

vim Dockerfile
Or,
nano Dockerfile
```

## Building Images: Running Docker Builds

* Check the docker sample 1 file.

```
Run: ll (LL small letter)

docker image build -t customnginx .

docker image ls

vim Dockerfile
Or,
nano Dockerfile

docker image build -t customnginx .
```
## Building Images: Extending Official Images
* Check the docker sample 2 file.
```
cd dockerfile-sample-2

Run: ll (LL small letter)

vim Dockerfile

docker container run -p 80:80 --rm nginx
Or,
docker container run -p 8080:80 --rm nginx

docker image build -t nginx-with-html .

docker container run -p 80:80 --rm nginx-with-html
Or,
docker container run -p 8080:80 --rm nginx-with-html

If you run 8080:80 prt then go to http://localhost:8080/ because only localhost will not work and we will not see our inde html file updates.

docker image ls

docker image tag --help

docker image tag nginx-with-html:latest codersh/nginx-with-html:latest

docker image ls

docker push
```


* Which of the following is an example of a container image that you can run?

  Answer: nginx

* Which flag would you pass to specify a docker build referencing a file other than the default 'Dockerfile'?

ANSWER: -f

 * Which Dockerfile stanza (Command) is best to use for changing the directory in a Dockerfile?

 ANSWER: WORKDIR


## Build Your Own Dockerfile and Run Containers :

 * Building our own image is quite fun part of the container images.
 * Docker file are part process workflow and part art.
 * Take exisiting Node.js app and dockerize it.
 * Make Dockerfile, build it, test it, push it, (rm it), Run it.
 * Expect this to be iterative, rarely do I get it right the first time. 
 * Details in dockerfile-assignment-1.Dockerfile.
 * Use the Alphine version of the official 'node' 6.x image.
 * Expected result is web site at http://localhost or, http://localhost:8080
 * Tag and Push to your docker hub account.
 * Remove the image from local cache, run again from hub.


```
cd dockerfile-assignment-1

vim Dockerfile

docker build cmd

docker build -t testnode .

docker container run --rm -p 80:3000 testnode

docker images

docker tag --help

docker tag testnode codersh/testing-node

docker push --help

docker push codersh/testing-node

docker image ls

docker image rm codersh/testing-node

docker container run --rm -p 80:3000 codersh/testing-node
```


