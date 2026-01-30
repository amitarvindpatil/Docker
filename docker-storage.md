### Docker Volume & Storage

when you run containers, all data inside the container filesystem is temporary.
if stop  or remove the container you may lose the data unless use the docker Storage mechanisms.

Two ways to pesists the data

    1. Bind Mount
    2. Volumes

- Bind Mount

`docker run -v /host/path:/container/path myimage`

        Bind Mount use a directory or file on    host machine and Mount it inside container  
        
        pros:
         -  Full control: choose the exact host path (/home/amit/data:/data)
         - Good for development
        cons:
         - Host dependent structure
         - no docker managed metadata

- Docker Volume 

`docker run -v myvolume:/var/lib/mysql mysql`

        Volume fully managed by docker and store under  

        - Linux/macOS: /var/lib/docker/volumes/
        - Windows: C:\ProgramData\Docker\volumes\

        pros:
            - Best for production
            - More Secure
            - Can be easily backup,migrate and easily use
            - Docker handles lifecycle,metadata,driver
        
        cons:
            - Not use directly in your project directory (use docker volume inspect)

#### Create Named Volume 

| command | Description     |
| :-------- | :------- | 
|`docker volume create appdata`| Create Volume
|`docker run -v appdata:/app/data myimage`| Use Volume
|`docker volume ls`| list volume
|`docker inspect volume`| inspect Volume

#### backup and restore volume

Backup Volume:

    We create a temporary container which mounts the volume and exports it as a .tar file.

    `docker run --rm -v mysql_data:/data -v $(pwd):backup alpine tar czvf /backup/mysql_data_backup.tar.gz /data`

    This Creates:
    ./mysql_data_backup.tar.gz


Restore Volume:

    Create New Volume:

    `docker volume create mysql_data`

    Restore the backup:

    `docker run -rm -v mysql_data:/data -v $(pwd):/backup alpine sh -c "cd /data && tar xzvf /backup/mysql_data_backup.tar.gz --strip 1" `
