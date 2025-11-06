
<h1> Spring Cloud Config Client</h1>

##  What is a Config Client?

>A Config Client is a microservice that connects to the Spring Cloud Config Server to fetch the applications configuration at startup.This ensures all services load centralized configuration stored in a remote repository (e.g., Git).


##  Steps to Configure a Spring Cloud Config Client

<h3>1. Add Config Client Dependency </h3>

```xml
<!-- https://mvnrepository.com/artifact/org.springframework.cloud/spring-cloud-config-client -->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-config-client</artifactId>
    <version>4.3.0</version>
</dependency>
```

<h3>2. Add Config Server URL  in microservice </h3>

In application.properties (or YAML):

```properties
spring.config.import=optional:configserver:http://myhost:8888
```

<h3>On Startup — Logs Example</h3>

```bash
INFO  --- ConfigServerConfigDataLoader : Fetching config from server at : http://localhost:8888
INFO  --- ConfigServerConfigDataLoader : Located environment: name=user-service, profiles=[default]
```
This indicates the microservice successfully contacted the Config Server and loaded configuration.


---

##  Question

<h2>1. Profile-Based Configuration </h2>

Rules : 

- For dev profile create `application-dev.properties `
- For prod profile create `application-prod.properties` 

<h4>1.1 If have multiple profile configuation file then how Configuration work?</h4>

suppose **user-service** uses a profile such as dev: `spring.profiles.active=dev`
The Config Server loads  from  `application.properties `and `application-dev.properties`

<h5>Log Example</h5>

```bash
The following 1 profile is active: "dev"
Fetching config from server at : http://localhost:8888
Located environment: name=user-service, profiles=[default]
Fetching config from server at : http://localhost:8888
Located environment: name=user-service, profiles=[dev]
```
  



<h2>2. How to Configure Data for a Specific Microservice with profile based ? </h2>


| Location                                | File   |
| --------------------------------------- | ------ |
| create config file of specific **profile**  | `application-dev.properties` , `applicaiton-prod.properties` |
| create config file of specific **microservice**        | `user-service.properties` , `order-service.properties` |
| create config file of specific **microservice and profile** | `user-service-dev.properties` |






<h2>3. Port Override Example</h2>

suppose for **user microservice**  has active **profile dev** and

| Location                                | Port   |
| --------------------------------------- | ------ |
| Local `application.properties`          | `8081` |
| Config Server `application.properties`  | `8082` |
| Config Server `application-dev.properties`          | `8083` |
| Config Server `user-service.properties` | `8084` |
| Config Server `user-service-dev.properties` | `8085` |

**Then,**

Final Port Used : 8085 
Because **service-specific + dev** config file has the highest priority.

 
<h2>4. suppose user-service has dev  profile  then how will configuration data ? </h2>

 If user-service has the dev profile active, Spring Cloud Config will load configuration files in a specific priority order.Only dev configs are considered.

| Load Order (Top = Highest Priority) | File                                                         |
| ----------------------------------- | ------------------------------------------------------------ |
| 1                               | `user-service-dev.properties` *(service + profile specific)* |
| 2                                 | `user-service.properties` *(service specific)*               |
| 3                                 | `application-dev.properties` *(global profile config)*       |
| 4                                 | `application.properties` *(global default config)*           |




<h2>5. Real-World Configuration Scenario</h2>

- Case  : 

    - Out of 10 microservices, 7 microservices share a property
    - 3 microservices need a different value

- Solution:

    - Put the common property in application.properties (config server) :   `app.owner=alamgir`

    - Override only for required services in their individual files
    service-specific override:
    service1.properties → `app.owner=service1`
    service2.properties → `app.owner=service2`
    service3.properties → `app.owner=service3`
