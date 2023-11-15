# Spring boot

### Spring boot features
- Fast bootstrapping 
- Autoconfiguration 
- Opinionated
- Standalone
- Production-ready

### Spring Boot components
- spring-boot
- spring-boot-autoconfigure
- spring-boot-starters
- spring-boot-CLI
- spring-boot-actuator
- spring-boot-actuator-autoconfigure
- spring-boot-test
- spring-boot-test-autoconfigure
- spring-boot-loader
- spring-boot-devtools

## Spring Boot Maven Plugin
To use Spring Boot Maven Plugin you have to add the following code in pom.xml of your project :

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>


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


## Spring data JPA
Initialize a database using Hibernate
**spring.jpa.hibernate.ddl-auto** : has this values 
- none : Hibernate doesn't perform any schema management. It expects the database schema to be pre-defined
- create : Hibernate creates a new database schema every time the application starts
- create-drop : Similar to the create option, Hibernate creates the schema at application startup. However, it drops the schema when the application shuts down. It's useful for testing environments where you need a fresh schema for each test run.
- update : Hibernate tries to update the existing schema based on changes in entity definitions. It adds new tables, columns, or constraints without dropping existing tables or data. This setting is suitable for development but might be risky in production environments as it can lead to data loss or inconsistencies.
- validate : Hibernate validates the entity mappings against the existing database schema but doesn't make any changes to the schema. It's a safe option for production as it ensures that the application and database schema are in sync without altering the schema

Conclusion :
- For production, using **validate** or **none** is generally recommended
- During development or testing, **create-drop** or **update** may be more suitable

Spring boot choose the default value based on database type (An embedded database is detected by looking at the Connection type: hsqldb, h2 and derby are embedded, the rest are not.)
- if  database is embedded (default create-drop)
- if (default none)


## Sequence :
allocationSize property to a value suitable for your use case. It specifies how many IDs will be pre-allocated in advance from the sequence.

    @Id
    @GeneratedValue(strategy = GenerationType.SEQUENCE, generator = "user_sequence")
    @SequenceGenerator(name = "user_sequence", sequenceName = "USER_SEQ", allocationSize = 1)
    private Long id;

## Disable data.sql for All Tests:

    @TestPropertySource(properties = {"spring.sql.init.mode=never"})

Or in application.properties
    
    spring.sql.init.mode=never

## Disable schema.sql for All Tests:

    @TestPropertySource(properties = {"spring.datasource.initialization-mode=never"})

Or in application.properties
    
    spring.datasource.initialization-mode=never


