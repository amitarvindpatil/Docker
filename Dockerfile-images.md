
####  What is Dockerfile

Dockerfile is a script containing instructions like (FROM,COPY,RUN) that docker use to build images

#### Dockerfile instructions
| Instruction | purpose     | example
| :-------- | :------- |:------- | 
|FROM|Base Image| `FROM python:3.10-slim`
|WORKDIR|working directory| `WORKDIR /app`
|COPY|copy file from machine to image | `COPY /app`
|ADD|copy but more powerful, extract the tar files,download the urls|`ADD https://example.com/file.tar.gz /app` 
|RUN|execute command during build and store result into image / use to install dependancies| `RUN yum update && yum install -y crul`
|CMD|Default command for container runtime |`CMD ["python","app.py"]`
|ENTRYPOINT| Set fix command that always run |`ENTRYPOINT ["python"]`| common pattern `ENTRYPOINT = executable, CMD = arguments`
|EXPOSE|Documents which port the container listen on | `EXPOSE 8080`| Note: EXPOSE doesnot publish the port. use -p during docker run
|ENV|Set Environment variable inside container|`ENV APP_URL=production`| Access using $APP_URL
|ARG|Define build-time arguments|`ARG VERSION=1.0  RUN echo $VERSION`| passing: `docker build --build-arg VERSION=2.0`
|VOLUME|Create mount point for persistent Storage| `VOLUME ["/data"]`
|USER|Set which user will run inside the container|`USER node` | best practice never use root
|LABEL|metadata about image|`LABEL maintainer="amit@gmail.com` `LABEL version="1.0"`| Useful for CI/CD or documentation
|HEALTHCHECK|checks container healthcheck|`HEALTHCHECK CMD curl --fail http://localhost:8080 || exit 1` | use in kubernetes
|SHELL|override Default shell|`SHELL ["powershell","-command"]`| Useful for windows
|STOPSIGNAL|docker which signal to send on docker stop | `STOPSIGNAL SIGTERM`
|ONBUILD|trigger Instruction when another build uses this image as FROM|`ONBUILD COPY . /app` | use for base images


####  MULTI-STAGE BUILD (multiple FROM instructions)
- Used to reduce image size
- Huge size reduction → Best practice.

      FROM node:18 AS builder
      WORKDIR /app
      COPY . .
      RUN npm install && npm run build
      
      FROM node:18-slim
      COPY --from=builder /app/dist dist/
      CMD ["node", "dist/server.js"]

####  Dockerfile Example

      FROM Ubuntu    <-- Start from base OS or another image

      RUN apt-get update      <-- install all dependancies
      RUN apt-get install python  
      RUN pip install flask
      RUN pip install flask-mysql

      COPY . /opt/source-code    <-- COPY source code
      ENTRYPOINT FLASK_APP=/opt/source-code/app.py   <-- Specify Entrypoint

#### Layerd Architecture
[Layerd Architecture]([https://example.com](https://github.com/user-attachments/assets/2cfe94ff-05f8-450c-abc2-74e001397cd3))


