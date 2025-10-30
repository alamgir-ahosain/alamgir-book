
<h1>Spring Framework Modules</h1>

## 1. Core Container Layer

- **1. core**:  
    - Consists of the **Core**, **Beans**, **Context**, and **SpEL** modules.  
    - Provides the core functionality (**IoC**, **Dependency Injection**).

- **2. beans**:  
    - Manages **beans (objects)** and their **life cycle**.  
    - A complex implementation of the **factory pattern** provided by the Bean module.

- **3. Context**:  
    - Builds on Core and Beans modules.  
    - Provides access to configured objects (**beans**).  
    - Main entry point: **ApplicationContext** interface for dependency injection.

- **4. SpEL (Spring Expression Language)**:  
    - Expression language for searching/querying/manipulating objects at runtime.  
    - Supports:
        - Property access  
        - Method calls  
        - Array/collection access  
        - Variable use  
        - Bean retrieval from IoC container  

---

## 2. AOP

- Provides **AOP (Aspect Oriented Programming)** features.

---

## 3. Aspect

- A module that encapsulates **cross-cutting logic**.  
- Example: A **logging aspect** that runs before/after methods.

---
## 4. Instrumentation

- Provides **class instrumentation** and **classloader implementations** for certain servers.  
- Configurable via:
   - XML  
   - Annotations (`@Aspect`, `@Before`, `@After`, etc.)  
   - AspectJ integration

---

## 5. Messaging

- Used for **asynchronous communication** between applications/components.  
- Supports:
   - **Point-to-point** (Queue)  
   - **Publish-subscribe** (Topic) models  
- Spring provides **spring-jms** for Java Messaging Service.

---
## 6. Data Access / Integration Layer

<h3>1. JDBC (Java Database Connectivity)</h3> 

- Contains a **JDBC abstraction layer**.  
- Simplifies JDBC code with **less boilerplate**.

<h3>2. ORM (Object-Relational Mapping)</h3>

- Integrates with ORM frameworks:
   - Hibernate  
   - JPA  
   - JDO  
   - iBatis  
- Supports **declarative transactions** for data persistence.

<h3>3. OXM (Object/XML Mapping)</h3>

- Supports mapping using:
  - JAXB  
  - Castor  
  - XMLBeans  
  - JiBX  
  - XStream

<h3>4. JMS (Java Messaging Service)</h3>

- Provides features for **producing/consuming** or **sending/receiving messages**.

<h3>5. Transaction</h3>


- Supports **programmatic** and **declarative** transaction management for **POJOs**.

---
## 7. Web Layer

- **1. web**: Basic web-oriented features (multipart file upload, REST clients).  
- **2. Web-Servlet**: **MVC (Model View Controller)** implementation for web applications.  
- **3. Web-Portlet**: MVC implementation for **portlet environments**; similar to Web-Servlet.  
- **4. websocket**: WebSocket and **real-time communication** support.  
- **5. Web-Struts**: Deprecated support for integrating **Struts**. Use **Struts 2.0** or **Spring MVC**.

---
## 8. Test Layer

- Supports testing Spring components with **JUnit/TestNG**.  
- Provides: **Applica**
<br>

[↑ Back to top](#top)
