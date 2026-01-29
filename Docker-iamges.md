
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

#### Full Workflow Example (Pull → Build → Tag → Push)

      Step 1: Pull base image
            - docker pull node:18

      Step 2: Build your app image
            - docker build -t myapp:v1

      Step 3: Tag it for docker hub
            - docker tag myapp:v1 amitpatil/myapp:v1

      Step 4: Login
            - docker login

      Step 5: push image
            - docker push amitpatil/myapp:v1
