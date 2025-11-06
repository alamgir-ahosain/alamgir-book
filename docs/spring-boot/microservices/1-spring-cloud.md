



<h2>What is Spring Cloud?</h2>

>Spring Cloud is a set of tools built on top of Spring Boot for building distributed microservices systems.


## Overview

- Spring Cloud is part of the Spring Boot ecosystem.
- It provides libraries and tools to build, configure, and manage microservice-based applications.

    - Makes microservices easier to manage, monitor, and scale.
    - Enables communication and coordination among services.

- It is not a cloud platform like AWS, GCP, or Azure — instead, it helps you build cloud-ready applications.




## Spring Cloud Core Components

| Component            | Purpose               |
| -------------------- | --------------------- |
| Eureka               | Service registry      |
| Spring Cloud Gateway | API gateway / routing |
| Config Server        | Centralized configuration        |
| Resilience4j         | Circuit breaker       |
| Sleuth               | Distributed tracing   |
| Zipkin               | Trace visualization   |
| Spring Cloud Stream  | Messaging             |





## Common Architecture Flow

```
Client -> API Gateway -> Eureka Discovery -> Microservices  
        -> Config Server -> Central Config Repo
        -> Zipkin / Sleuth -> Tracing
        -> Kafka/RabbitMQ -> Async Events
```        

![Spring Boot Microservices Architecture ](<diagram-spring-cloud.png>)