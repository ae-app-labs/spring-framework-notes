# Profiles
Profiles are a way to manage application configuration for different environments or different runtime conditions. Profiles allow you to define sets of configuration that are activated based on the environment in which the application is running. This enables you to easily switch between configurations for development, testing, production, and other scenarios.

## 1. Profile Activation:
- Profiles can be activated in several ways:
  - By setting the `spring.profiles.active` property in application.properties or application.yml.
  - By setting an environment variable (SPRING_PROFILES_ACTIVE).
  - By specifying profiles as command-line arguments when starting the application.

## 2. Profile-Specific Configuration:
- Configuration files can be named based on profiles, such as application-dev.properties or application-prod.yml. These files will be loaded when the corresponding profile is active.
```yml
# application-dev.yml
server:
  port: 8081
```
- You can define profile-specific configurations using application-{profile}.properties.
```properties
# application-dev.properties
server.port=8081
```

## 3. Default Profile:
You can have a default configuration in application.properties or application.yml that is applied when no profiles are explicitly activated.
```yml
# application.yml
server:
  port: 8080
```

## 4. Profile-Specific Beans:
- You can use the @Profile annotation on @Bean methods to conditionally create beans based on active profiles.
```java
@Configuration
public class MyConfiguration {
    @Bean
    @Profile("dev")
    public DataSource devDataSource() {
        // dev-specific configuration
    }

    @Bean
    @Profile("prod")
    public DataSource prodDataSource() {
        // prod-specific configuration
    }
}
```

## 5. Application-Profile YAML Documents:
- You can use YAML documents to specify profiles and their configurations in a single file.
```yaml
# Common configuration
server:
  port: 8080

---

# Dev profile configuration
spring:
  profiles: dev
server:
  port: 8081
```

## 6. Profile-Specific External Configuration:
External configuration properties, such as those provided through command-line arguments or environment variables, can also be profile-specific.
```bash
java -jar myapp.jar --spring.profiles.active=dev
```

