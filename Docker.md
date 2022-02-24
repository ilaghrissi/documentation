# Docker

### Docker commands 

| Command                               | Comment                                                                                                                                                                                              |
|---------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| docker images                         | Show images                                                                                                                                                                                          |
| docker container ls                   | Show containers                                                                                                                                                                                      |
| docker inspect <container_name>       | Show additional information about a container (print out a long json)                                                                                                                                |
| docker ps                             | Show all running containers                                                                                                                                                                          |
| docker logs <container_name>          | Show logs of selected container                                                                                                                                                                      |
| docker container rm <container_name>  | Remove a specific container                                                                                                                                                                          |
| docker image rm <image_name>          | Remove a specific image                                                                                                                                                                              |
| docker exec -it <container_name> bash | Run shell inside the container, the bash process will have the same Linux namespaces as the main container process <br/> -i : make sure STDIN kept open <br/> -t : allocates a pseudo terminal (TTY) |
| ps aux                                | Exploring container to see the process running in the container                                                                                                                                      |
| docker-compose up                     | Create the Docker image and start application using docker compose created                                                                                                                           |
| docker-compose down                   | Stop docker container                                                                                                                                                                                |



### Docker by example : Run Spring boot application in docker 

#### Basic Method with only Dockerfile

1. create Dockerfile in root of your project :


    FROM openjdk:openjdk:8-jdk-alpine
    MAINTAINER tutorials team
    VOLUME D:/tmp
    ARG WAR_FILE=/*.war
    ADD ${WAR_FILE} app.war
    ENTRYPOINT ["java","-jar","/app.war"]

2. Build :


    docker build --tag=my-app:latest .

3. Run :


    docker run --name my-app-container -p 8887:8888 my-app:latest

This will start our application in Docker, and we can access it from the host machine at localhost:8887/.
<br/>
-p8887:8888 means :  maps a port on the host (8887) to the port inside Docker (8888)


4. Tag the image :

    
    docker tag my-app tutorials/my-app

tutorials : is your own ID in docker hub

6. Push the image in docker hub

    
    docker push tutorials/my-app

7. Run the image from different machine


    docker run -p 8080:8080 -d tutorials/my-app

8. Pull the image from docker hub

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