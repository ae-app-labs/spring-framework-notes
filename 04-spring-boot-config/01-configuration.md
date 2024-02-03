# Configuration
In a Spring Boot application, the `application.properties` and `application.yml` files are commonly used for configuring various aspects of the application. These files allow you to externalize configuration from your code, making it easier to manage and modify settings without changing the application's code.

## `application.properties`
### Key-Value Pairs:
- Configuration properties are defined as key-value pairs.
```properties
server.port=8080
spring.datasource.url=jdbc:mysql://localhost:3306/mydatabase
```

## `application.yml`
### Indentation
- YAML uses indentation for structuring data.
```properties
server:
  port: 8080
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/mydatabase
```

## Usage in Spring Boot
### Accessing Properties in Code
- Use `@Value` annotation to inject properties into Spring beans.
```java
@Value("${server.port}")
private int serverPort;
```
- Configuration can be externalized using command-line arguments, environment variables, or custom property files.
```bash
java -jar myapp.jar --server.port=9090
```
