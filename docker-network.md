### Docker Network

Default Networks :

1. Bridge Network (Default)
    - Default for containers
    - NAT-based
    - provide isolation
    - support internal DNS 

    | command | Description     |
    | :-------- | :------- | 
    |`docker network ls`|List Network
    |`docker run -d --name web --network bridge nginx`| Run container on bridge
     
2. Host Network 
    - Fast Network
    - No port mapping needed
    - less isolation

    Container port 80 is host's port 80
    | command | Description     |
    | :-------- | :------- | 
    |`docker run --network host nginx`| Run container on host

3. None Network 
    - No internet
    - No DNS
    - completely isolation
    
    command: `docker run --network none alpine`


#### Exposing Ports -p vs -P 

`-p` publish on specific port 

format: host_port:container_port

command: `docker run -p 8080:80 nginx`

`-P` publish on all high ports

command: `docker run -P nginx`
check assign ports: `docker ps`

### custom network creation

command: `docker network create mynetwork

Run container on this network: 

`docker run -d --name c1 --network mynetwork nginx`

`docker run -d --name c2 --network mynetwork alpine sleep 5000`

now c2 --> can ping --> c1

### Inspect Network

`docker network inspect mynetwork`

#### connect/disconnect network

    docker network connect mynetwork c2
    
    docker network disconnect mynetwork c1


