### What is Docker Compose?

Docker Compose is use to define,run and manage multi-container application using a single YAML file (Docker-Compose.yml)

Declare the service (api,web,db etc.), how they connect (networks), and where the data store(volumes), then run it into single command.

`docker compose up -d`
### docker compose run --link commands
`docker run -d --name=redis redis`

`docker run -d --name=db`

`docker run -d --name=db`

`docker run -d --name=vote -p 5000:80 --link redis:redis`

`docker run -d --name=result -p 5001:80 --link db:db`

`docker run -d --name=worker --link db:db --link redis=redis`

### Docker compose useful commands

Bring up/tear Down

    docker compose up -d        # stops & removes containers, networks (not named volumes)
    docker compose down   # also removes named volumes (data loss!)
    docker compose down -v

Rebuild & restart

    docker compose build --no-cache
    docker compose up -d --build

Scale

    docker compose up -d --scale api=3

Status,Logs and shell

    docker compose ps
    docker compose logs -f api
    docker compose exec api sh

Enviroment Profile

    docker compose --profile dev up -d

### docker-compose.yml - Strcture and key Section

docker-compose-example.yml :- https://github.com/amitarvindpatil/Docker/blob/main/docker-compose-example.yml

Example will done after lab


