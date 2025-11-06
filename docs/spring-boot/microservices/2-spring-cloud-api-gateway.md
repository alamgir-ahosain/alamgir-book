
<h1> Spring Cloud API Gateway</h1>


##  Introduction 
>API Gateway is the single entry point for all microservices. It receives client requests, routes them to the appropriate service, and returns the response. It acts as the primary contact for all incoming client requests.






| Function             | Description                                     |
| -------------------- | ----------------------------------------------- |
| Routing              | Sends requests to the correct microservice      |
| Load Balancing       | Distributes traffic across service instances    |
| Security             | Authentication, Authorization, JWT              |
| Rate Limiting        | Controls number of requests (prevents overload) |
| Logging & Monitoring | Tracks requests and responses                   |
| Transformation       | Modify request/response (headers, body, URL)    |





---

##  API Gateway Implementation

<h3>1. Add Gateway Starter Dependency</h3>

 Add the **Spring Cloud Gateway (Reactive)**  dependency in `pom.xml`

```xml
    <dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-gateway-server-webflux</artifactId>
    </dependency>
```        

<h3>2. Configure Routing for Microservices</h3>

Routing can be configured in two ways:

- Programmatic : 	Define routes using a `@Bean`
- Properties / Declarative	: Define routes in `application.properties` or `application.yml`


    <h4>2.1  Routing Using application.properties</h4>

    Example route for User Microservice

    ```properties

    # user microservice
    spring.cloud.gateway.server.webflux.routes[0].id=user-service
    spring.cloud.gateway.server.webflux.routes[0].uri=http://localhost:8081
    spring.cloud.gateway.server.webflux.routes[0].predicates[0]=Path=/user/**
    ```

---

##  Example 

API Gateway Configuration
```properties
spring.application.name=api-gateway
server.port=8080
```

User Service Endpoint : http://localhost:8081/user/create
Call the user-service API via the gateway as : http://localhost:8080/user/create


| Request via Gateway                   | Routes to backend service URL     |
| ------------------------------------- | --------------------------------- |
| http://localhost:8080/user/create | http://localhost:8081/user/create |



Then,

<h4>1. Flow </h4>

- The gateway will receive this request at `/user/create `, match the `predicate /user/** `
- proxy route it to the user-service running at http://localhost:8081/user/create. 
- Gateway routes predicate's `Path=/user/**` decides which URLs get forwarded.



<h4>2. Gateway Logging</h4>

When a request hits the API Gateway,  logs like:

```terminal

GET "/user/read", parameters={}
Mapped to HandlerFilterFunction
Completed 200 OK
```
This means:

- Request` /user/read `came to gateway
- Gateway forwarded it to `User Service`
- Response returned successfully 

