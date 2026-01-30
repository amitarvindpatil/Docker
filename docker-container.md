
####  Docker Container

docker container is a lightweight, standalone, and executable package that contains everything need to run an application- code,runtime,os,libraries,system tools etc

#### Docker containers essentials commands 
| command | Description     |
| :-------- | :------- | 
|`docker start <container_id>`| Start a container 
|`docker stop <container_id>`| stop running container
|`docker restart <container_id>`| restart container
|`docker rm <container_id_name>`| remove or delete container
|`docker rm -f <container_id_name>`| remove forcefilly container
|`docker container prune`| remove all stop container

#### default path of docker cotnainer logs 

`/var/lib/docker/containers/<container-id>/<container-id>-json.log`


### Detached  vs Interactive Mode

#### Detached mode (-d) -
 runs the container in background mode

command: `docker run -d <container_id>`

usecase :- runing servers (nginx,MySQL Redis)

#### Interactive Mode (-it) - 

-i : keep STDIN open

t : attach to a pseudo terminal

command: `docker run -it ubuntu bash`

Interactive shell inside the container

usecase: debugging, Runnning shell based task , Exploring Images

### Logging And debugging tools

view container logs : `docker logs <container_id_or_name>`

follow logs like tail -f : `docker logs -f <container_id_name>`

Execute into running container : `docker exec <container_id_or_name>`

To get a shell : `docker exec -it <container_id_or_name> bash`

To get a alpine : `docker exec -it <container_id_or_name> sh`

Insepct container metadata (IP/mount-volumes/env vars): `docker inspect <container_id_or_name>`

### Resouce Limits (CPU & Memory)

Docker allows restriciting container resouces using flags during docker run

Limiting Memory: `docker run -m 512 --memory-swap=512m ubuntu`

Limiting CPU (Limit CPU usage to 50% of a single CPU:) : `docker run --cpus="0.5" ubuntu`

combine CPU & Memory : `docker run -d -m 512m --cpus="1.0" nginx`
