## These are some docker commands and their use


1. **Docker pull**

Used to download an image. But doesn't run the image

Syntax: 
```sh
docker pull <image name|:[tag]>
```
Example: 
```sh
docker pull redis
```


2. **Docker run** 

Used to run an image. Download the image if not present on the system.

Syntax: 
```sh
docker run <image name|:[tag]>
```
Example: 
```sh
docker run redis:6.2.7
```

Example: 
```sh
docker run --name redis-latest redis:6.2.7
```


3. **Docker ps**

Used to display running containers

Syntax:
```sh
docker ps
```

To display stop containers as well

```sh
docker ps -a
```

4. **Docker stop**
Used to stop a container


Syntax:
```sh
docker stop <image name | image ID>
```

Example:

```sh
docker stop redis-latest
```

5. **docker rm**

Used to remove a stopped container

Syntax:
```sh
docker rm <container name | container ID>
```

Example:

```sh
docker rm redis-latest
```

6. **Docker rmi**

Used to remove a downloaded image

Syntax:
```sh
docker rmi <image name | image ID>
```

Example:

```sh
docker rmi redis-latest
```

7. Expose a port

Syntax:
```sh
docker run <image name | image ID> --name <container name> -p <host port : container port>
```

Example:

```sh
docker run --name redis-server -p 8080:6379 redis:latest
```

8. Docker images

Used to list downloaded images

Syntax:
```sh
docker images
```

9. Run in detached mode

To run oin detached mode use the `-d` option

Example:

```sh
docker run --name redis-server -p 8080:6379 -d redis:latest
```

10. Display the container's logs

Example:

```sh
docker logs <container name | container ID>
```

11. Access the container shell

Use the `exec` command usually coupled with the `-it` option

Syntax:
```sh
docker exec -it <container name | container ID> <command to run>
```

Example:

```sh
docker exec -it redis-latest /bin/sh
```

12. Inspect an image or a container

Syntax:
```sh
docker inspect <image name | image ID | container name | container ID>
```

Example:

```sh
docker inspect redis-latest
```

13. Clear all images and configurations

Syntax:

```sh
docker system prune -a
```

14. Help

Syntax:
```sh
docker [subcommand] --help
```

Example:
```sh
docker --help
docker run --help
```