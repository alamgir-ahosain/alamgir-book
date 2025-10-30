<h1>Spring JDBC</h1>

## 1. JDBC (Java Database Connectivity)

> A powerful mechanism to connect to the database and execute SQL queries.
<h2 id="">Problems with JDBC</h2>

- A lot of boilerplate code.
- Exception Handling Problem (multiple try-catch-finally block).
- Code duplication.
- Database login is a time consuming task.

## 2. Spring JDBC

- Provides a JDBC abstraction layer through the JdbcTemplate class.
- Simplifies JDBC code with less boilerplate.
- Provides jdbcTemplate class which has all the important methods to perform operations with database.
- Integrates easily with Spring’s IoC container (dependency injection).

<h2 id="">Key Components</h2>
<h3 id="">1. DataSource</h3>

- Interface type
- Used to manage database connection properties (username, password, url).
- Contains:
    - `driverClassName` = ? (for MySql → com.mysql.jdbc.Driver)
    - `url` = ? (jdbc:localhost:8080)
    - `username` = ?
    - `password` = ?

<h3 id=""> 2. DriverManagerDataSource</h3>

- Implementation of DataSource

##  3. JdbcTemplate

> JdbcTemplate is a Spring Framework class that simplifies interaction with relational databases.

- Pre-defined and Bean type class.
- It is created using an `@Bean` method (not with `@Component`, since it’s a predefined Spring class).
- Helper class for simpler JDBC database access.
- Removes boilerplate (connection, statement, resultset handling).
- Converts SQLExceptions to Spring’s DataAccessException.
- Automatically manages resource closing and exception translation.


<h3 id="">Common Methods in JdbcTemplate</h3>

- `update()` : INSERT, UPDATE, DELETE
- `query()` : SELECT returning multiple rows
- `queryForObject()` : SELECT returning a single row/value
- `batchUpdate()` : Bulk operations

##  4. Manually JdbcTemplate Configuration (Spring)

- Manually create Bean objects.
- JdbcTemplate defined in a Configuration class with an `@Bean` method.
- DataSource configured with url, username, and password.
- Use JdbcTemplate: Predefined classes exposed via `@Bean`, not `@Component`.

<h3 id=""> Steps to Use</h3>

- Create and configure `DriverManagerDataSource` (set driver class, DB URL, username, and password)
- Inject DataSource into `JdbcTemplate`
- Use JdbcTemplate to perform database operations (`query()`, `update()`, `execute()`, etc.)



##  5. JdbcTemplate Configuration in Spring Boot

- Auto-configuration enabled by `@SpringBootApplication` (includes `@EnableAutoConfiguration`).
- Add dependency: `spring-boot-starter-jdbc`.
- JDBC driver (jar) added to classpath via dependency automatically.
- JdbcTemplate Bean auto-created using `spring.datasource.*` and taking properties (url, username, password) from `application.properties` file.

<h2 id=""> Steps to Use</h2>

Using JDBC in Spring Boot

- Add JDBC driver:  (`Oracle: ojdbc`,` MySQL: MySQL connector`, `PostgreSQL: pg jar`).
- Configure database in `application.properties` (URL, username, password, driver).
- Use `JdbcTemplate` for queries: query(), queryForObject(), update(), batchUpdate().
- Resource management is automatic (connections opening and closing , exceptions handled by Spring).




##  6. What is ResultSet?

- A Java object that represents the data returned from a SQL query.
- Created when executing a SELECT statement.
- Acts like a cursor that points to rows in the result.

<h3 id="">Common Methods</h3>

- `next()` : Move to next row (returns true if row exists)
- `getString("columnName")` : Get column value as String
- `getInt("columnName")` : Get column value as int

- `getDate("columnName")` : For other types
- `close()` : Free the ResultSet resources

##  7. RowMapper

- `RowMapper<T>` is a Spring interface.
- It maps each row of a ResultSet into a Java object (T).
- Makes code cleaner by avoiding direct ResultSet handling.
- Commonly used with `JdbcTemplate.query()` and `queryForObject()`.
- Example: Convert rows from `studentTable` into `Student` objects

The Interface

```java
public interface RowMapper<T> {
    T mapRow(ResultSet rs, int rowNum) throws SQLException;
}
```

* `rs` : current row of the ResultSet
* `rowNum` : row number (starting from 0)
* Returns : the mapped object (e.g., a Student object)

1.**For single Object:** `public queryForObject(String sql,RowMapper<T> rowMapper,Object args)`

```java
    Student student = jdbcTemplate.queryForObject(
        "SELECT * FROM studentTable WHERE id=?",
        new StudentRowMapper(),
        id
    );
```

2.**For multiple Objects:** `public List<T>query(String sql,RowMapper<T>rowMapper)`

```java
    List<Student> students = jdbcTemplate.query(
        "SELECT * FROM studentTable",
        new StudentRowMapper()
    );
```


##  8. What is BeanPropertyRowMapper?


* A built-in implementation of RowMapper.
* Automatically maps columns in a ResultSet to Java object fields (POJO).
* Uses JavaBean property naming (setters/getters).

```java
class Student{
    private int id ;
    private String name;
    // setters and getters methods
}

@Component
class Operation{

    @Autowired
    private JdbcTemplate jdbcTemplate;

    public void readAll(){
        List<Student> students = jdbcTemplate.query(
            "SELECT * FROM studentTable",
            new BeanPropertyRowMapper<>(Student.class)
        );
    }

}
```
<br>

[↑ Back to top](#top)<br><br>
   
>**Github Code** : [Spring JDBC : spring ](https://github.com/alamgir-ahosain/Learn-Spring-Framework/tree/main/k_spring_jdbc)
<br>

>**Github Code** : [Spring JDBC : spring Boot ](https://github.com/alamgir-ahosain/Learn-Spring-Boot/tree/main/d-jdbc)

