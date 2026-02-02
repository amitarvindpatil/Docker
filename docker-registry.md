### Docker Registry

Docker hub is a default public Registry used by Docker

### Private Registry
    1. Docker Registry (Open Source)
    2. AWS ECR
    3. Google container Registry (GCR)
    4. Azure container Registry (ACR)

 benifits :

    Secure and access control
    Fast image pull in CI/CD 
    version control for internal microservices

### Run your own private registry:
`docker run -d -p 5000:5000 --name registry registry:2`

Push/pull example:

    
    docker tag myapp:latest localhost:5000/myapp
    docker push localhost:5000/myapp
    docker pull localhost:5000/myapp

Authentication:

`docker login`

`docker login myregistry.com` - private registry (username/password or tocken required)


Pushing image

    Step1: Tag image
           docker tag myapp:1.0 myregistry.com/myteam/myapp:1.0
    
    Step2: Push image
            docker push myregistry.com/myteam/myapp:1.0

Pull image:
    docker pull myregistry.com/myteam/myapp:1.0

### Full Push and Pull Workflow

push:

    docker build -t myapp .
    docker tag myapp myregistry.com/project/myapp:v1
    docker login myregistry.com
    docker push myregistry.com/project/myapp:v1

pull:

    docker login myregistry.com
    docker pull myregistry.com/project/myapp:v1
