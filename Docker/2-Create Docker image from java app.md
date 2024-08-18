Here is how to create a docker image from a java application. The following commands are usually written in a specific file named `Dockerfile`. But it is not mandatory to name the file like that.

# Useful commands

1. FROM

Used to define the basic layer. It is good to go from a smaller image when possible

Syntax:
```sh
FROM <image:[tag]>
```

Example:
```sh
FROM openjdk:17

# or for smaller image
FROM alpine
```

2. ARG

Used to define an argument that can be use in the Dockerfile

Syntax:
```sh
ARG <argumentName>=<argumentValue>
```
To use the value stored in the variable, use the syntax `${argumentName}`

Example:
```sh
ARG JAR_FILE=target/*.jar
```

3. COPY

Copy a file from the file system to the image file system

Syntax:
```sh
COPY <source> <destination>
```

Example:
```sh
COPY ${JAR_FILE} app.jar
```

4. ENTRYPOINT

To run a command when the image starts, use `ENTRYPOINT`.
CMD` can also be used

Syntax:
```sh
ENTRYPOINT ["cmd1", "cmd2", ..., "cmdn"]
```

Example:
```sh
ENTRYPOINT ["java", "-jar", "app.jar"]
```

5. EXPOSE ports
Syntax:
```sh
EXPOSE <port>
```

Example:
```sh
EXPOSE 8080
```


6. Docker login

Used to login from the command line

Commands:
```sh
docker login

#or
docker login -u <username> -p<password>
```


7. Docker push

To push a local image to your remote repository

Syntax:
```sh
#make sure the name of the image is in the forme username/imageName
docker push <imageName:tag>
```

 

Example:
```sh
docker push myrepo/myapp:latest
```

# Example of a docker file

Name of the file: `Dockerfile` located at the root of the app

```sh
FROM openjdk:17

ARG JAR_FILE=target/*.jar

COPY ${JAR_FILE} app.jar

ENTRYPOINT ["java", "-jar", "app.jar"]

EXPOSE 8080
```


To build the image, don't forget to build the maven app
```sh
mvn clean install
```

And then build the docker image

Syntax:
```sh
docker build -t <username/imageName:tag> . 
```

Example:
```sh
docker build -t myrepo/my-java-app:latest -t myrepo/my-java-app:0.0.1 . 
```



Continue to:

- [[3-Docker-compose]]

