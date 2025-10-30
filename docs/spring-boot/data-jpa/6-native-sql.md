
<h1 id="top">Native SQL Query</h1>

## 1. Native Query

- Written in `plain SQL`.
- Works directly with database tables and columns.
- Database-specific (`not portable`).


<h4>Rules for creating native query</h4>

- Create an abstract method inside Repository interface.
- Define return type of an entity class.
- on top of abstract method define `@Query` annotation.
 

## 2. @Query
 
>configuring required SQL query to be executed.

<h4>2 mandatory parameter</h4>

- **Value** : query(String format)
- **nativeQuery** : boolean property(default is false)
    - **true** : JPA undertand given query is SQL language.
    - **false** : it's JPQL not native SQL.

Example
```java
public interface UserRepository extends JpaRepository<User, Integer> {
   
    @Query(value = "SELECT * FROM USER", nativeQuery = true)
    List<User> getAllUser();
}
```    
```sql
Hibernate: SELECT * FROM USER
```
Hibernate directly sent to the query(as it is,no changes) in DB level.

## 3. Query Parameters

Two type of Query parameters :

1. Indexed Query Parameter
2. Named Query Parameter 

<h3>1. Indexed Query Parameter</h3>

* Syntax: `?<indexNumber>`
* Index `starts from 1`
* Define method parameters as part of the abstract method.


Repository Example

```java
public interface UserRepository extends JpaRepository<User, Integer> {
   
    @Query(value = "SELECT * FROM user WHERE NAME=?1", nativeQuery = true)
    List<User> getUserByName(String name);
}
```
Method Example

```java
public void getUserByNameMethod(String name) {
    List<User> users = userRepository.getUserByName(name);
    users.forEach(System.out::println);
}
```



<h4> Multiple Index Parameters</h4>

> Make sure the **order of method parameters** is the same as the column values.

Repository Example

```java
public interface UserRepository extends JpaRepository<User, Integer> {
   
    @Query(value = "SELECT * FROM user WHERE NAME=?1 AND EMAIL=?2", nativeQuery = true)
    List<User> getUserByNameAndEmail(String a, String b);
}
```
Here,

- ?1 binds to the first method argument (a)
- ?2 binds to the second method argument (b)


Method Example

```java
public void getAllUserParamsMethod(String name, String email) {
    List<User> users = userRepository.getUserByNameAndEmail(name, email);
    users.forEach(System.out::println);
}
```




 <h3>2. Named query parameter.</h3>

 - Avoid confusion of parameters order.
 - Order doesn’t matter when using named params.
 - Increase Readbility.
 - `@Param` binds a repository method’s argument to a named parameter (`:paramName`) in a JPQL or native SQL query.

 Syntax  `:parameterName`

 Example
```java
public interface UserRepository extends JpaRepository<User, Integer> {
  
    @Query(value = "SELECT * FROM USER WHERE EMAIL=:myEmail AND NAME=:myName", nativeQuery = true)
    List<User> getUserByNameAndEmailNamed(@Param("myName") String a, @Param("myEmail") String b);
}
``` 


key points

- First argument is annotated with `@Param("myName")` → it will bind to `:myName `
- Second argument is annotated with `@Param("myEmail")` → it will bind to `:myEmail` 
- Java variable names(`String a,String b`) doesn’t matter.
- only the` @Param("...")` values must match the query placeholders.

```java
public void loadUserByNameAndEmailNamed(String name, String email) {

        List<User> users = userRepository.getUserByNameAndEmailNamed(name, email);
        users.forEach(System.out::println);
    }
```

## 4. @Modifying

>@Modifying tells Spring Data JPA that a @Query changes data (INSERT, UPDATE, DELETE) instead of reading it.

Key points:

- Used with @Query for update/delete operations.
- Often combined with @Transactional.
- Returns number of affected rows.

Example
```java
 @Modifying
    @Query(value = "DELETE FROM user WHERE NAME = ?1", nativeQuery = true)
    int deleteByName(String name);
```
<br>

[↑ Back to top](#top)   <br><br>


>**Github Code** : [CRUD Operation](https://github.com/alamgir-ahosain/Learn-Spring-Boot/tree/main/e-crud-opeation) 
