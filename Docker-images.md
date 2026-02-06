
#### Docker Images
Docker image is Read-Only template that contains everything need to run an application inside container

It includes
   - application code
   - Dependancies
   - Runtime (python/java/node etc.)
   - Libraries 
   - configurations
   - OS level files

####  Difference between docker images and Container

| Docker Images | Docker Container     |
| :-------- | :------- | 
|Blueprint| Running instance
|ReadOnly| Read/Write Layer
|Stored in Registry| Run on Docker Engine
|Can create Multi-Container| One isolated runtime



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

### Check history of image
| command | example     |
| :-------- | :------- | 
|`docker history image_name`|`docker history nginx`

### Inspect Image
| command | example     |
| :-------- | :------- | 
|`docker inspect image_name`|`docker inspect nginx` | showes env,vars,layers

### clean all Image
| command | example     |
| :-------- | :------- | 
|`docker system prune -af` | Remove all images

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

#### How do you reduce Docker Image size?  ***
- Use #### MultiStage Builds
- Use small base images (alpine, slim)
- Clean Cache (rm -rf /var/lib/apt/list/*)
- use .dockerignore
- remove build tool after installation

#### How to scan an image for vulnerabilities?
Tools :
   - docker scan
   - Trivy   `trivy image nginx:latest `
   - Clair
#### What is scratch images
   smallest possible image__ an empty base used for static binaries

      FROM scratch 
      COPY app /app
      CMD ["/app"]

#### Difference Docker Save and Docker Export
   Docker Save : Save the image

   Docker export : Save container filesystem (no layer/history)
