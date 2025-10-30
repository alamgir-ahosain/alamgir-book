
<h1>Spring Bean Life Cycles</h1>

## 1. What is  Spring Bean Lifecycle?

- Lifecycle of an individual bean managed by the container.
- key annotation : `@PostConstruct`, `@PreDestroy`, `InitializingBean`, etc.
- Includes : Instantiation, Dependency Injection, Init & destroy callbacks.

## 2. Life Cycle Method

   1. Instantiation – Spring creates the bean object.
   2. Populate properties / Dependency Injection – Spring injects values or references.
   3. BeanNameAware / BeanFactoryAware callbacks – Optional callbacks if implemented.
   4. Pre-initialization – `@PostConstruct` or` afterPropertiesSet()` (from InitializingBean).
   5. Custom init method – Optional method defined by `init-method`.
   6. Bean is ready to use – Application uses the bean.
   7. Destruction – Container shuts down; `@PreDestroy`, `destroy()` (from `DisposableBean`), or `destroy-method` is called.         


## 3. Ways to Define Lifecycle Methods

**1. Using xml**

   - Spring provide two method to every bean .
   - Good for 3rd-party or external classes.
   - we can change the name of these method but signature must be same
     - `public void init()`: Called after creation via config.Initialization code loading config,connecting db,webservice .
     - `public void distroy()`:For clean up code

<Details>
<Summary>Example Code</Summary>

   ```java
   <bean id="student" class="Student" init-method="init" destroy-method="cleanup"/>
   public class Student {

      public void init() {
         System.out. println("Bean is initialized");
      }
      public void cleanup() {
         System.out.println("Bean is destroyed");
      }

   }
   ```
</Details>

**2. Using Interface**

   - `afterPropertiesSet()` : called after dependencies are injected.
   - `destroy()` : called when container shuts down.


<Details>
<Summary>Example Code</Summary>

```java
@Component
 public class Student implements InitializingBean, DisposableBean {
          
            @Override
            public void afterPropertiesSet() throws Exception {
               System.out.println("Bean is initialized");
            }

            @Override
            public void destroy() throws Exception {
               System.out.println("Bean is destroyed");
       }
    }
```   
</Details>


**3. Using Annotation**

   - Recommended modern approach
   - `@PostConstruct` : Called after bean is created & dependencies injected
   - `@PreDestroy` : called before bean is removed from container.


<Details>
<Summary>Example Code</Summary>

```java
@Component
public class Student {
         public Student(){}
         @PostConstruct
         public void init() {
            System.out.println("Bean is initialized");
         }

         @PreDestroy
         public void cleanup() {
            System.out.println("Bean is destroyed");
         }

         public void init2(){
            System.out.println("Bean is initialized again");
         }

         public void cleanup2() {
            System.out.println("Bean is destroyed again");
     }
 }


public class AppConfig{
   @Bean(initMethod = "init2", destroyMethod = "cleanup2")
   public Student student2(){
      return new Student();
   }
}
```

</Details>


All 4 methods will be called, in this order:

1. Initialization Order (on startup):
   - `@PostConstruct` : `init()`
   - `@Bean(initMethod = "...")` : `init2()`

2. Destruction Order (on shutdown):
      - `@PreDestroy` : `cleanup()`
      - `@Bean(destroyMethod = "...")` : `cleanup2()`




## 4. Question

**1. Is it possible to execute logic when a bean object created?**

YES,Ways to Execute Logic After Bean Creation:

   - `init-method `in XML or `@Bean`
   - `@PostConstruct` using annotation
   - `InitializingBean.afterPropertiesSet()` using interface


**2. Difference Between singleton and prototype scope (Bean Lifecycle Perspective)**

1. Singleton

      - Created once at container startup
      - `@PreDestroy` / `destroy()` : Called by Spring when context is closed
      - Bean Destruction Responsibility : Spring container

2. Prototype

      - Created every time the bean is requested.
      - `@PreDestroy` / `destroy() `: Not called automatically
      - Bean Destruction Responsibility : must be handle manually.


<br>

[↑ Back to top](#top)<br><br><br>
>**Github Code** : [Bean Life Cycle : Spring ](https://github.com/alamgir-ahosain/Learn-Spring-Framework/tree/main/d_bean_lifecycle_annotations)
