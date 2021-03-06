# Spring boot

## Spring Boot Maven Plugin

| Command                                                                                                                                | Description                                                                                                                                              |
|----------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| mvn spring-boot:run                                                                                                                    | Run Spring boot application                                                                                                                              |
| mvn spring-boot:run -Dspring-boot.run.profiles=local                                                                                   | Run Spring boot application with profile local                                                                                                           |
| mvn spring-boot:run -Dspring-boot.run.profiles=local,dev                                                                               | Run Spring boot application with multiple profiles local and dev                                                                                         |
| mvn spring-boot:run -Dspring-boot.run.profiles=local -Dspring.config.location=file:///C://dev/application.config.properties            | Run Spring boot application with profile local and override configs (only take external configs internal will not be token)                              |
| mvn spring-boot:run -Dspring-boot.run.profiles=local -Dspring.config.additional-location=file:///C://dev/application.config.properties | Run Spring boot application with profile local and add additional configs (internal and external will be token if the same config priority  to external) |

## Run spring boot application with java command

| Command                                                                                                                            | Description                                                                                                                                              |
|------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| java -jar app.jar                                                                                                                  | Run Spring boot application                                                                                                                              |
| java -jar app.jar --spring.profiles.active=local                                                                                   | Run Spring boot application with profile local                                                                                                           |
| java -jar app.jar --spring.profiles.active="local,dev"                                                                             | Run Spring boot application with multiple profiles local and dev                                                                                         |
| java -jar app.jar --spring.profiles.active=local --spring.config.location=file:///C://dev/application.config.properties            | Run Spring boot application with profile local and override configs (only take external configs internal will not be token)                              |
| java -jar app.jar --spring.profiles.active=local --spring.config.additional-location=file:///C://dev/application.config.properties | Run Spring boot application with profile local and add additional configs (internal and external will be token if the same config priority  to external) |
