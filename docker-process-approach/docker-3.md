# Container Lifetime & Persistent Data: Volumes, Volumes, Volumes

## Persistent Data: Data Volumes

* Important Resources to learn: ```bit.ly/3hy1YXy``` or, 
```https://bit.ly/3xE53e8``` Or, ```https://bit.ly/3k5u8KW``` Or, ```https://dockr.ly/3AQcFw4``` Or, 
```https://jekyllrb.com/```
* Defining the problem of persistent data.
* Key concepts with containers : immutable, ephemeral
* Learning and isng data volumns and bind Mounts.
* Containers are usually immutable and ephemeral.
* "immutable infrastructure": only re-deploy containers that never change.
* Defintion of persistent data.
* Features of seperation docker concerns.
* Two ways: Volumes and bind mounts.
* Volumes: makes special location outside of container UFS.
* Bind Mounts: links to container path to host path.
* Which type of persistent data allows you to attach an existing directory on your host to a directory inside of a container?
ANSWER: Bind Mount
* When adding a bind mount to a docker run command, you can use the shortcut $(pwd), (or ${pwd} depending on your shell). What does that do?
ANSWER: It runs the shell command to print the current working directory, to avoid having to type out the entirety of your directory location.
This command stand for "print working directory", and shortens your keystrokes, and reduces errors from mistyping your path or forgetting to escape spaces in the path.
* When making a new volume for a mysql container, where could you look to see where the data path should be located in the container?
ANSWER: Docker Hub

* VOLUME commans in Dockerfile.

```
docker pull mysql

docker image inspect mysql

docker container run -d --name mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=True mysql

docker container ls

docker container inspect mysql

docker volume ls

docker volume inspect TAB COMPLETION

docker container run -d --name mysql2 -e MYSQL_ALLOW_EMPTY_PASSWORD=True mysql

docker volume ls

docker container stop mysql

docker container stop mysql2

docker container ls

docker container ls -a

docker volume ls

docker container rm mysql mysql2

docker volume ls

docker container run -d --name mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=True -v mysql-db:/var/lib/mysql mysql

docker volume ls

docker volume inspect mysql-db

docker container rm -f mysql

docker container run -d --name mysql3 -e MYSQL_ALLOW_EMPTY_PASSWORD=True -v mysql-db:/var/lib/mysql mysql

docker volume ls

docker container inspect mysql3
or,
docker volume inspect mysql-db

docker volume create --help
To remove:
docker container rm -f mysql

```

## Persistent Data: Bind Mounting
* Maps a host file or directory to a container file or directory.
* Basically just two locations pointing to the same files
* Again skipping UFS and host files overwrite any containers 
* Cannot use in dockerfile, must be a ```container run```. 
* ...run -v /Users/codersh.stuff:/path/container

```
cd dockerfile-sample-2

pcat Dockerfile
Or,
cat Dockerfile

docker container run -d --name nginx -p 80:80 -v $(pwd):/usr/share/nginx/html nginx
Or,
docker container run -d --name nginx -p 8080:80 -v $(pwd):/usr/share/nginx/html nginx

Go to : http://localhost:8080/

docker container run -d --name nginx2 -p 8080:80 nginx
Or, 
docker container run -d --name nginx2 -p 8081:80 nginx

docker container exec -it nginx bash
```
### Database Upgrades with Named Volumes
* Database upgrade with container
* Create a postgres container with named volume psql-data using version 
* Use Docker Hub to learn VOLUME path and versions needed to run it. 
* Check logs, stop container.
* Create a new postgres container with same named volume using 9.6.2
* Check logs to validate.
```
docker container run -d --name psql -v psql:/var/lib/postgresql/data postgres:9.6.1

docker container logs -f psql

docker container stop TAB-COMPLETION

docker container ps -a

docker volume ls

docker container logs TAB-COMPLETION
```

## Assignment: Edit Code Running In Containers With Bind Mounts

```
ll

cd bindmount-sample-1

docker run -p 80:4000 -v $(pwd):/site codersh/jekyll-serve

Or,
docker run -p 8080:4000 -v $(pwd):/site codersh/jekyll-serve
```
### Database Passwords in Containers :
```
For docker run, and the forthcoming Docker Compose sections, you need to either set a password with the environment variable:

POSTGRES_PASSWORD=mypasswd

Or tell it to ignore passwords with the environment variable:

POSTGRES_HOST_AUTH_METHOD=trust

Note this change was in the Docker Hub image, and not a change in postgres itself.
```
### Shell Differences for Path Expansion 
```
With Docker CLI, you can always use a full file path on any OS, but often you'll see me and others use a "parameter expansion" like $(pwd) which means "print working directory".

Here's the important part. Each shell may do this differently, so here's a cheat sheet for which OS and Shell your using. I'll be using $(pwd) on a Mac, but yours may be different!

This isn't a Docker thing, it's a Shell thing.

For PowerShell use: ${pwd} 

For cmd.exe "Command Prompt use: %cd%

Linux/macOS bash, sh, zsh, and Windows Docker Toolbox Quickstart Terminal use: $(pwd) 

Note, if you have spaces in your path, you'll usually need to quote the whole path in the docker command.
```
