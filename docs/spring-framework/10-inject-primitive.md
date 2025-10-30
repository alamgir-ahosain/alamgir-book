
<h1> Inject Primitive and String Type</h1>

## 1. Application Properties</h1>

- Always configuring data which is commonly being used by all spring Beans.
- Called as Configuration file.
- key value pair format(key-val).
- two types of properties
    - pre-defiend(spring.application.name)
    - used defiend(db.name=alamgir)

Example `application.properties` file:

```properties
spring.application.name=b-dependency-injection
db.port=8080
db.url=localhost:8080
db.password=mysql
db.database=mysql,oracle,postgres
```

## 2. Using @Value Annotation

<h4> Injecting values directly:</h4>

```java
@Value("8080")
private int port;

@Value("localhost:8080")
private String url;
```

<h4>Injecting from properties:</h4>

```java
@Value("${db.password}")
private String password;
```

<h4>Default Values</h4>

```java
@Value("${db.name:mysql}")
private String name;
```
If the property is missing, the default value `mysql` will be used.

<h4>Injecting Multiple Values</h4>

For list-type properties:

```java
@Value("${db.database}")
private List<String> database;
```

 If `db.database=mysql,oracle,postgres` : it becomes a list: `[mysql, oracle, postgres]`


 **How it works:**

1. Spring checks `application.properties` (or `application.yml`).
2. Looks for the property.
    * If  Found : proceeds.
    * If Not found : throws `java.lang.IllegalArgumentException: Could not resolve placeholder 'db.password'.`
3. Injects the value into the field.


## 3. Using @PropertySource

Add external `.properties` files:

```java
@Configuration
@PropertySource("classpath:db.properties")
public class AppConfig { }
```

<h3> Key Points</h3>

* `@PropertySource` tells Spring where to load a `.properties` file from.
- Used on  a @Configuration class.
* Works with `@Value("${property.name}")`.
* Can load multiple files:
    ```java
    @Configuration
    @PropertySource("classpath:db.properties")
    public class AppConfig { }  
    ```
    `classpath:` looks inside `src/main/resources`.
* If a property exists in **both** `application.properties` and a `@PropertySource` file:
    - Spring Boot **uses the value from application.properties**.
    - `@PropertySource` has **lower priority** than default Spring Boot property files.<br>

    [↑ Back to top](#top)<br><br><br>
    >**Github Code** : [Inject primitives and String type : Spring Boot](https://github.com/alamgir-ahosain/Learn-Spring-Boot/tree/main/b-dependency-injection/src/main/java/com/alamgir/b_dependency_injection/inject_primitives)



