
<h1>Service Discovery </h1>

>Service Discovery allows microservices to automatically register themselves and discover other services through the Service Registry (Eureka) instead of hard-coded URLs.

<h4>Key Points</h4>

- Register each microservice as a Discovery Client
- Discovery Client enables microservices to locate other services dynamically via the registry


##   Service Discovery Client Setup (Eureka Client)

<h3>1. Add starter dependenct : Eureka Client </h3>

```xml
<!-- https://mvnrepository.com/artifact/org.springframework.cloud/spring-cloud-starter-netflix-eureka-client -->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
    <version>4.3.0</version>
</dependency>
```

<h3>2. Enable Discovery Client Annotation</h3>

In each microservice main class : add  annotation `@EnableDiscoveryClient`

```java
@EnableDiscoveryClient
@SpringBootApplication
public class UserServiceApplication {

	public static void main(String[] args) {
		SpringApplication.run(UserServiceApplication.class, args);
	}
}
```

<h3>3. Add Service Registry URL (in each microservice)</h3>

 suppose service registry url : `http://localhost:8761/`

```properties

# Service Registry URL
eureka.client.service-url.defaultzone=http://localhost:8761
```

<h4>Successful Registration Log Sample</h4>

 > 2025-11-01T16:35:55.783+06:00  INFO 46780 --- [service-registry] [nio-8761-exec-4] c.n.e.registry.AbstractInstanceRegistry  : Registered instance USER-SERVICE/fedora:user-service:8081 with status UP (replication=true)

---

##  API Gateway as Discovery Client 

Enable Gateway application also as Discovery Client and then


<h3>1. Enable Discovery in Gateway</h3>

```properties
spring.cloud.gateway.discovery.locator.enabled=true
```

<h3>2.  Routing setup</h3>

<h5>1. Manual Routing Example</h5>

```bash
http://localhost:8080/user/create
http://localhost:8080/order/create
```

<h5>2. Dynamic Routing Format</h5>

Syntax : `gatewayhostName:portNumber/<serivce-id>/<end-point>`

```bash
 localhost:8080/USER-SERVICE/user/create
 localhost:8080/ORDER-SERVICE/order/create
``` 

<h5>3. Service Name Case</h5>

Eureka converts service IDs to UPPERCASE
To use lowercase IDs:    

```properties
spring.cloud.gateway.discovery.locator.lower-case-service-id=true
```
Then

```bash
http://localhost:8080/user-service/user/create
http://localhost:8080/order-service/order/create
```



##  Dynamic Routing 

>Dynamic Routing allows the gateway to automatically discover and route requests to microservice instances without manual configuration.

If user-service has multiple instances (8081, 8082, 8083):

- Without discovery client → manually configure all instances 
- With discovery client → all instances auto-detected 
- If one instance goes down → Gateway auto-routes to available instance .

>No manual routing required. Eureka + Gateway handles it.



## Load Balancing     

>Load Balancing distributes incoming traffic across multiple service instances to ensure performance, reliability, and no single server overload.

When client hits API Gateway:

- Gateway checks service registry for available instances
- Uses load-balancing algorithm (ex: Round-Robin)
- Sends request to the least busy instance

##  Overview 

| Concept               | Description                                                                              | Dependency / Annotation                                          |
| --------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| Service Registry  | Central registry that stores and manages all microservice instances                      | `spring-cloud-starter-netflix-eureka-server` *(Eureka Server)*   |
| Service Discovery | Mechanism that allows microservices to find and communicate with each other via registry | `spring-cloud-starter-netflix-eureka-client` *(Eureka Client)*   |
| Discovery Client | A microservice that registers itself with the service registry automatically             | `@EnableDiscoveryClient` *(or included auto with Eureka Client)* |
