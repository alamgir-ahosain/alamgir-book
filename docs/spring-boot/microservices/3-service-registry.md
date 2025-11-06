<h1> Service Registry </h1>

>Service Registry is a centralized system that stores and manages all microservices' location and status. It registers each microservice and helps them discover each other.

 Key Points

- Central registry for all microservices
- Collects and maintains service information (name, port, IP, status)
- Allows microservices to discover each other (Service Discovery)
- Eliminates hard-coded service URLs
- Keeps track of service availability & health




##  Enable Service registry — Eureka Server provied by Netflix 

<h3>1. Add Eureka server dependency</h3>

```xml
    <dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
    </dependency>
```    

<h3>2. Set Server Port (default: 8761) </h3>

```properties
server.port=8761
```
<h3>3. Enable Eureka Server in Main Class</h3>

```java
@EnableEurekaServer
@SpringBootApplication
public class ServiceRegistryApplication { 
    public static void main(String[] args) {
        SpringApplication.run(ServiceRegistryApplication.class, args);
    }
}
```
<h3>4. Disable Self-Registration (Optional, Recommended for server)</h3>

By default, Eureka Server tries to register as a discovery client application.
Disable this behavior:

```properties
eureka.client.fetch-registry=false
eureka.client.register-with-eureka=false
```

<h3>5. Access Eureka Dashboard : http://localhost:8761/</h3>

##  Note

>By default ,Microservice are not  going to register with service registry (Eureka). We must enable them as discovery clients separately. 
> **using Eureka client dependency**



