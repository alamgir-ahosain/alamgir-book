<h1>Microservices Communication</h1>

>Microservice communication refers to how independent services in a microservice architecture interact and exchange data. In Spring Boot, this communication can be synchronous or asynchronous .


## Key Points

| Type                           | Description                                                            | Common Tools                                                  |
| ------------------------------ | ---------------------------------------------------------------------- | ------------------------------------------------------------- |
| Synchronous Communication  | Real-time request/response between services                            | REST (WebClient/RestTemplate), Feign Client,gRPC |
| Asynchronous Communication | Services communicate via events/messages; no immediate response needed | Kafka, RabbitMQ, ActiveMQ, SNS/SQS          |


| Scenario                    | Best Option         |
| --------------------------- | ------------------- |
| Real-time request           | REST / Feign / gRPC |
| High traffic & async events | Kafka / RabbitMQ    |
| Cross-language services     | gRPC                |
| Simple synchronous calls    | REST                |


![ Microservice Communication ](<diagram-microservice-communication.png>)

---

##  Feign Client in Spring Boot

>OpenFeign is a declarative HTTP client used in Spring Boot microservices to call other services easily using simple Java interfaces — no manual RestTemplate or boilerplate code needed,integrating seamlessly with Service Discovery (like Eureka).



<h1>Implementation Steps</h1>

<h3>1. Add Depedency : OpenFeign</h3>

Add the OpenFeign dependency in  consumer service (the service that calls another).

```xml
<!-- https://mvnrepository.com/artifact/org.springframework.cloud/spring-cloud-starter-openfeign -->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-openfeign</artifactId>
    <version>4.3.0</version>
</dependency>
```

<h3>2.Enable Feign Clients</h3>

Enable Feign support by adding  annotation `@EnableFeignClients` on  consumer  application class.

```java
@EnableFeignClients
@EnableDiscoveryClient
@SpringBootApplication
public class OrderServiceApplication {

	public static void main(String[] args) {
	SpringApplication.run(OrderServiceApplication.class, args);
	}
}
```

<h3>3. Create Feign Client Interface</h3>

Each microservice which want to call should have its own Feign client interface.


> @FeignClient Annotation : Declares that a REST client should be created for the interface.If Spring Cloud LoadBalancer is available, it automatically load-balances backend requests.


Steps:

- Add @FeignClient("producer-service-id") → the microservice name from Eureka.
- Define abstract methods matching the target API.
- Use @RequestMapping / @GetMapping / @PostMapping to map endpoints.
- Keep return types compatible with API responses.

<Details>
<Summary>Producer Service Endpoint</Summary>

```java
//Access : localhost:8080/payment-service/payment/check
@GetMapping("/check")
    public List<Payment> getAllPaymentDetails() {
        return paymentService.getAllPaymentDetails();
    }
```    
</Details>


<Details>
<Summary>Consumer Feign CLient</Summary>
 
```java
    @FeignClient("payment-service")
    public interface PaymentMicroserviceFeginClient {

     // Consumer API : localhost:8080/payment-service/payment/check
     @RequestMapping(method = RequestMethod.GET,path = "/payment/check")
     List<PaymentResponse> checkAllPayment();
    }
```
</Details>



<h3>4. Expose Controller Endpoint</h3>

Expose a controller method to test Feign client communication.


```java
    //!Feign Client
    @GetMapping("/check/payment/v2")
    public List<PaymentResponse> checkAllPaymentv2() {
        return orderService.checkAllPaymentv2();
    }
```

<h3>5. service class </h3>

```java
    //! FeignClient
    public List<PaymentResponse> checkAllPaymentv2() {
        return paymentMicroserviceFeginClient.checkAllPayment();
    }
```


Access Example

```sql
Producer (Payment Service): localhost:8080/payment-service/payment/check
Consumer (Order Service):  localhost:8080/order-service/payment/check/v2
```

---

##  How Feign Client Works Internally ?


When a Feign Client is called, it performs several internal steps automatically:

 Step-by-Step Flow
 
- Takes the Service ID
From the @FeignClient annotation (e.g. "payment-service").

- Contacts the Service Registry
Sends a request to the Service Registry (Eureka) to find instances of that service.

- Checks for Available Instances
If any instance of the producer service is registered, Eureka returns their details
(e.g. localhost:8080, localhost:8082).

- Load Balancer Selects One
Spring Cloud LoadBalancer picks one instance (default: round-robin).

- Builds the Actual URL
Example: http://localhost:8080/payment/check

- Sends the HTTP Request
Feign uses an internal HTTP client (like Apache HttpClient or OkHttp) to call the API.

- Maps the Response
The JSON response is automatically converted into the defined return type.


>Feign takes the service ID → looks up Eureka → finds a live instance → load-balances → makes the HTTP call → returns the response.
