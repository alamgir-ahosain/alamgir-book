
<h1>spring cloud Config Server</h1>





##  Scenario

<h4>Problem: Distributed Microservices, Duplicate Configurations</h4>

In a microservices environment, each service often maintains its own configuration:
- Database credentials (name, URL, username, password)
- Environment properties
- Common service URLs (e.g., Registry, Gateway)

<h4>Main Points</h4>

- Configuration duplication across services
- High maintenance effort — updating a property in multiple services
- Risk of inconsistency in shared config values
- Difficult to manage changes across environments (dev/test/prod)



##  Solution — Centralized  Config Server

>A Config Server stores all microservice configuration centrally and supplies it at runtime.

Benefits

- Externalized configuration
- Single source of truth
- No duplication
- Easy updates (change once → used by all services)


>Microservice → Fetch config from Config Server on startup → Load config into memory

 Config Server Architecture

| Component          | Role                                                       |
| ------------------ | ---------------------------------------------------------- |
| **Config Server**  | Serves configuration files to microservices                |
| **Git Repository** | Stores actual config files (application.properties / YAML) |
| **Config Client**  | Microservice that fetches config at startup                |


##  Implementing Spring Cloud Config Server

<h3>Supported Config Sources</h3>

- GitHub / Git repo (recommended)
- Local file system
- Database (not common)


<h3>1. Add starter Dependency</h3>

```xml
 <!-- https://mvnrepository.com/artifact/org.springframework.cloud/spring-cloud-config-server -->
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-config-server</artifactId>
        <version>4.3.0</version>
    </dependency>  
```    

<h3>2. Enable Config Server :</h3>

Add annotation `EnableConfigServer`

```java
@EnableConfigServer
@SpringBootApplication
public class ConfigServerApplication {

	public static void main(String[] args) {
		SpringApplication.run(ConfigServerApplication.class, args);
	}
}
```

<h3>3. Accour an exception </h3>

Terminal : 
  >  If you are using the git profile, you need to set a Git URI in your configuration.  
   > If you have set spring.cloud.config.server.bootstrap=true, you need to use a composite configuration.      

<h3>4. Example Config File in GitHub</h3>


Create application.properties inside  Git repo


```properties
    # Database Setup for PostgreSQL
    spring.datasource.url=jdbc:postgresql://localhost:5432/springdb
    spring.datasource.username=postgres
    spring.datasource.password=postgresql
    spring.datasource.driver-class-name=org.postgresql.Driver
    # Service Registry URL
    eureka.client.service-url.defaultzone=http://localhost:8761
```



<h3>5.  Configure Config Server (application.properties)</h3>


```properties
spring.application.name=config-server
server.port=8090
server.servlet.context-path=/config

# Git Repo URL
spring.cloud.config.server.git.uri=https://github.com/alamgir-ahosain/Learn-Spring-Boot.git

```

<h3>6. Test Config Server</h3>

Access URL: http://localhost:8090/config/app/default

<Details>
<Summary>Sample JSON output</Summary>

```json
{
  "name": "app",
  "profiles": ["default"],
  "propertySources": [
    {
      "source": {
        "spring.datasource.url": "jdbc:postgresql://localhost:5432/springdb",
        "spring.datasource.username": "postgres",
        "spring.datasource.password": "postgresql",
        "eureka.client.service-url.defaultzone": "http://localhost:8761"
      }
    }
  ]
}
```
</Details>