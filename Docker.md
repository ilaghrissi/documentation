# Docker

### Docker commands 

| Command                              | Comment                                                                    |
|--------------------------------------|----------------------------------------------------------------------------|
| docker images                        | Show images                                                                |
| docker container ls                  | Show containers                                                            |
| docker logs <container_name>         | Show logs of selected container                                            |
| docker container rm <container_name> | Remove a specific container                                                |
| docker image rm <image_name>         | Remove a specific image                                                    |
| docker-compose up                    | Create the Docker image and start application using docker compose created |
| docker-compose down                  | Stop docker container                                                      |



### Run Spring boot application in docker 

#### Basic Method with only Dockerfile

First off all create Dockerfile in root of your project :

    FROM openjdk:openjdk:8-jdk-alpine
    MAINTAINER tutorials team
    VOLUME D:/tmp
    ARG WAR_FILE=/*.war
    ADD ${WAR_FILE} app.war
    ENTRYPOINT ["java","-jar","/app.war"]

Build :

    docker build --tag=my-app:latest .

Run :

    docker run -p8887:8888 my-app:latest

This will start our application in Docker, and we can access it from the host machine at localhost:8887/.
<br/>
-p8887:8888 means :  maps a port on the host (8887) to the port inside Docker (8888)

Others useful commands : 

    docker inspect my-app
    docker stop my-app
    docker rm my-app


#### Method with Dockerfile and docker-compose.yml 
create docker-compose.yml in root of your project : 

    version: "3"
    services:
     my-app:
      image: tutorial/my-app:latest
      ports:
        - "8081:8081"