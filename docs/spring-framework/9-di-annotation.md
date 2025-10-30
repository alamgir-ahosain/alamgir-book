
<h1 id="top"> DI and Autowiring via Annotation/Java Based Configuration</h1>


<h1 id="intro">Three main ways to inject dependencies via Annotation:</h1>

1. Field / Property Injection  
2. Constructor Injection  
3. Setter Injection  



<h2>What is Autowiring?</h2>

Autowiring is automatic injection of dependencies by Spring. Instead of manually linking beans in `XML` or `Java config`, Spring can detect and inject them automatically.


<h2>What is Field Injection?</h2>

Putting the `@Autowired` annotation directly on a class field,  
so Spring injects the dependency without using setters or constructors.


## 2. @Autowired Annotation

* Tells Spring to automatically inject a bean into another bean,  
* letting the IoC container resolve and provide the dependency at runtime.  
* Injects only reference types (beans), not primitives or Strings.  
* can be applied to: Fields, Setter methods and Constructors.  
* No control of Programmer.  



<h3>@Autowired Resolution Rules </h3>

* Primary rule : `byType`  
* If multiple beans of that type exist : Try `byName` resolution.  
   * checks field name / parameter name with bean ID.  
   * If a match is found then bean is injected.  

* If still ambiguous : throws `NoUniqueBeanDefinitionException` (can fix with `@Qualifier` or `@Primary`)  

<Details>
<Summary>Example Code</Summary>

```java
      package com.spring;
      @Component
      public class Address{
         public void Address(){}
      }

      package com.spring.pkg;
      @Component("myStudent")
      public class Student{
            @Autowired // Field Injection
            public Address address;

            public void Student(){}
            public Address getAddress(){return address;  }
      }


      @Configuration
      @ComponentScan("com.spring") 
      class AppConfig{   
      }


      class Test{
         ApplicationContext container = new AnnotationConfigApplicationContext(AppConfig.class);  
         Student s = container.getBean("myStudent", Student.class);
      }
```
</Details>


<h3>How it works:</h3>

1. Spring scans the package.
2. Finds Address and Student as `@Component` beans.
3. Injects Address into Student’s address field automatically.


<h2>Question </h2>

Given
Dependency Type : `Address`
Available beans: `address`, `address1`

<h4>Case 1: Student : Address address</h4>

1. type = Address (two beans exist).
2. Field name=`address` matches bean id `address`
3. DI success : injects `address`

<h4>Case 2: Student : Address address1</h4>

1. type = Address (two beans exist).
2. Field name = `address1`  matches bean id `address1`.
3. DI Success: injects `address1`

<h4>Case 3: Student : Address xyz</h4>

1. type = `Address` (two beans exist).
2. Field name = `xyz` but no matching bean id.
3. DI Failed: throws `NoUniqueBeanDefinitionException`

---

## 3. Ambiguity Problem

Plain Java : Ambiguity arises with overloaded constructors + null arguments.

In Spring, if define multiple constructors,
Spring doesn’t know which constructor to use for injection, leading to an error.

```java
@Component
class Student {
   private String name;
   private int age;
   public Student(String name) {this.name = name; }
   public Student(int age) {  this.age = age; }
}

```


Spring cannot figure out whether to call Student(String) or Student(int) when creating the bean.


<h2 id="ways">3.1 Ways to solve Ambiguity</h2>

<h4>1. Mark the intended constructor with @Autowired</h4>

```java
@Component
class Student {
   private String name;

   @Autowired
   public Student(String name) {this.name = name;} // Spring will use this
   public Student(int age) { }  //spring Not used for Dependency Injection
}

```


<h4>2. Use @Qualifier to tell Spring which bean to inject</h4>

- `@Qualifier` resolves conflicts(ambiguity) when multiple beans of the same type exist.
- Must match `bean id` or bean name exactly.
- used with `@Autowired` for constructor, setter, or field/property  injection.
- which bean id is quialified for DI process.
- Acts like `ref` attribute in XML perspective.


<Details>
<Summary>Example Code</Summary>

   ```java
   // Address Class
   package com.spring;
   @Component("address1")
   public class Address{
   public void Address(){}
   }

   //Student Class
   package com.spring.pkg;
   @Component("myStudent")
   public class Student{

      @Autowired 
      Qualifier("address2")
      public Address address;
      public void Student(){}
   }

   //AppConfig Class
   @Configuration
   @ComponentScan("com.spring") 
   class AppConfig{ 

      @Bean
      public Address address2(){
         return Address();
      } 
      @Bean
      public Address address3(){
         return Address();
      } 
   }

   ```

</Details>



 <h4>3. Use @Primary Annotation</h4>

- Marks a bean as default when multiple beans of same type exist.
- Works with `@Autowired` to avoid ambiguity.
- Can be used on a class (`@Component`) or a method (`@Bean`).

```java
@Bean
@Primary
public String defaultName() {
   return "Default Name";
}

```

---

<h1>Remember:</h1>

* Avoid overloaded constructors in Spring-managed beans.
* Best practice: define only one constructor for injection.


## 4. DI with Interface and Implements


<Details>
<Summary>Scenario</Summary>

```java
class Vehicle(){
    public String type();
}


@Component
class Car implements Vehicle(){
    @override
    public String type(){return "type :Car"}
}

@Component
class Bike implements Vehicle(){
    @override
    public String type(){return "type is Bike"}
}

@Component
class Garage(){

    @Qualifier("bike")
    @Autowired
    private Vehicle vehicle;
}

```
</Details>


<h3>What happens?</h3>

1. spring scan for beans.
2. creates bean object(`car`,`bike`,`garage`).
3. Garage class need a Vehicle
    - `@Autowired` + `@Qualifier("bike")` tells Spring:Don’t just pick any Vehicle, inject the bean with name bike. So Spring injects the Bike object.

4. Result 
      - Inside Garage, the vehicle field refers to the Bike bean.
      - Calling `vehicle.type()` will return: `type is Bike`



---
## 5. Priority between @Qualifier and @Primary

- @Qualifier : Has higher priority (explicit match).
- @Primary : Used only if no @Qualifier is specified.
- If neither is used : `NoUniqueBeanDefinitionException` when multiple beans exist.

So **@Qualifier overrides @Primary**.


## 6. Relation among @Autowired ,@Qualifier and @Primary

* `@Autowired` → performs injection.
* If multiple beans → Spring looks for` @Qualifier`.
* If no `@Qualifier` → Spring falls back to `@Primary`.
* If neither → `NoUniqueBeanDefinitionException`.<br>
[↑ Back to top](#top)<br><br><br>


>**Github Code** : [DI via Annotation : Spring Boot](https://github.com/alamgir-ahosain/Learn-Spring-Boot/tree/main/b-dependency-injection
)