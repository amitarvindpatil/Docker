
#### Docker Images
Docker image is Read-Only template that contains everything need to run an application inside container

It includes
   - application code
   - Dependancies
   - Runtime (python/java/node etc.)
   - Libraries 
   - configurations
   - OS level files

### How to pull Images/ download image
| command | example     |
| :-------- | :------- | 
|`docker pull <image-name>:<tag>`| `docker pull nginx:latest`
|`docker run <image-name>`| `docker run nginx`

### push an Image 

| command | example     |
| :-------- | :------- | 
|`docker push <image-name>:<tag>`|`docker push username/myapp:v1`

before push login first
command : `docker login`

### remove docker image
| command | example     |
| :-------- | :------- | 
|`docker rm <image-name>:<tag>`|`docker rmi myapp:v1`

