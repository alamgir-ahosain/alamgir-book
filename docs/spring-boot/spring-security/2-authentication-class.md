<h1 id="top"> Important Classes & Their Roles in JWT Authentication</h1>





## 1. UserDetails

- An **Interface** representing a Spring Security user.
- Maps  user entity to Spring Security.
- Purpose: Provide authentication-related info to Spring Security.
- Key methods to implement:

    - `getUsername()` → return unique username/email
    - `getAuthorities()` → return roles/permissions
    - `isAccountNonExpired()` → account validity
    - `isAccountNonLocked()` → account lock status
    - `isCredentialsNonExpired()` → credentials validity
    - `isEnabled()` → account enabled/disabled

<Details>
  <Summary>Example</Summary>

  ```java

  @Entity
  public class User implements UserDetails {

    @Id
    private String email;
    private String password;

    @Override
    public Collection<? extends GrantedAuthority> getAuthorities() { return null; }

    @Override
    public String getUsername() { return email;}
  }
  ```

</Details>

## 2. UserDetailsService

- An **Interface** used by Spring Security to load user information during authentication.
- Returns a **UserDetails** object.
- Usually implemented in a service class.
- Key methods to implement:

    - `UserDetails loadUserByUsername(String username) throws UsernameNotFoundException`


>UserDetailsService bridges  database user entity and Spring Security for authentication.

<Details>
<Summary>Example</Summary>

```java

@Component
public class UserAuthenticationServiceImpl implements UserDetailsService {

   @Autowired
  UserRepository userRepository;
  
  @Override
  public UserDetails loadUserByUsername(String email) throws UsernameNotFoundException {

      // load data from DB for a specific user
       Optional<User> user = userRepository.findByEmail(email);
       If (user.isPresent()) { return user.get();  }
       else throw new UsernameNotFoundException("Email not Found :" + email);
    }
}
```
</Details> 




## 3. AuthenticationManager

- **Role:** Core interface responsible for authenticating user credentials.
- **Key Functionality:**

    - Returns Authentication on success, throws `BadCredentialsException` on failure.
    - Uses configured authentication providers (like `DaoAuthenticationProvider`) to validate credentials.

- **Usage:** Called in the login controller or authentication service.
 
 
Example 

```java
Authentication authentication = authenticationManager.authenticate(
    new UsernamePasswordAuthenticationToken(username, password)
);
```

## 4. BCryptPasswordEncoder

- **Role:** Encrypts passwords using the BCrypt hashing algorithm.
- **Key Functionality:**

    - Provides `encode()` to hash passwords.
    - Provides `matches()` to verify raw password against hashed one.

example

  ```java
  passwordEncoder.encode(password);
  passwordEncoder.matches(rawPassword, encodedPassword);
  ```


## 5. SecurityFilterChain

- **Role:** Defines the security configuration and registers custom filters.
- **Key Functionality:**

    - Replaces deprecated `WebSecurityConfigurerAdapter`.
    - Defines which endpoints require authentication and which are public.
    - Registers custom filters (like `JwtAuthenticationFilter`).

- **Usage Example:**

<Details>
<Summary>example</Summary>

  ```java
  @Bean
  public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
      http.csrf().disable()
          .authorizeHttpRequests()
          .requestMatchers("/auth/**").permitAll()
          .anyRequest().authenticated()
          .and()
          .addFilterBefore(jwtAuthFilter, UsernamePasswordAuthenticationFilter.class);
      return http.build();
  }
  ```
</Details>


## 6. OncePerRequestFilter

- **Role:** Base class for custom filters executed **once per HTTP request**.
- **Key Functionality:**

    - Intercepts each HTTP request.
    - Used to create custom filters like `JwtAuthenticationFilter`.
    - Extracts and validates JWT from the header.
  - Sets authentication in the SecurityContextHolder if valid.

- **Usage:** Added to the Spring Security filter chain before - `UsernamePasswordAuthenticationFilter`.

example

```java
String token = request.getHeader("Authorization");
if (token != null && jwtService.validateToken(token)) {
    // set authentication context
}
filterChain.doFilter(request, response);
```



## 7. SecurityContextHolder

- **Role:** Holds the security context (authentication details) for the current thread.
- **Key Functionality:**

    - Associates a given SecurityContext with the current execution thread.
    - Stores `Authentication` object once user is successfully authenticated.
    -  Provides global access to authentication info anywhere in the app.

- **Important Methods**:

    - `getContext()` → Gets the current security context.
    - `setContext(SecurityContext context)` → Sets a new context.
    - `clearContext()` → Clears authentication info.

Example

  ```java
  Authentication auth = SecurityContextHolder.getContext().getAuthentication();
  ```


## 8. UsernamePasswordAuthenticationToken

- **Role:** Represents the authentication object used to hold username and password credentials.
- **Key Functionality:**

    - Used to pass login credentials to `AuthenticationManager`.
    - Carries login data (username, password).
    - After authentication, stores authorities (roles).

-  Important Methods:

      - `getPrincipal()` → Returns username.
      - `getCredentials()` → Returns password.
      - `setAuthenticated(boolean isAuthenticated)` → Marks the authentication status.

example

  ```java
  Authentication auth = new UsernamePasswordAuthenticationToken(username, password);
  ```

## 9. FilterChain

- **Role:** Manages the flow of multiple filters during an HTTP request.
- **Key Functionality:**

    - Passes the request/response to the next filter.
    - Allows or blocks access based on authentication.
- Important Methods:

  - `doFilter(ServletRequest request, ServletResponse response)` → Passes the request to the next filter.

Example

```java
  filterChain.doFilter(request, response);
```








## 10.  Flow in JWT Authentication

- User sends credentials → verified by AuthenticationManager.
- UserDetailsService loads user data from DB.
- BCryptPasswordEncoder validates password.
- JWT token generated and returned to user.
- On each request:

    - `OncePerRequestFilter` validates token.
    - `SecurityContextHolder` stores authentication.
    - `SecurityFilterChain` manages which requests are secured.


  <br>
  
  [↑ Back to top](#top) 