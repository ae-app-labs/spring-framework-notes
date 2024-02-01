# Spring Bean Scopes
In Spring, bean scopes determine the lifecycle and visibility of a bean within the Spring IoC container. The scope of a bean defines how long the bean lives and how it's shared among different parts of the application. Spring provides several built-in bean scopes, and you can also create custom scopes if needed.

## Common Spring Bean Scopes
1. Singleton (default):
- Only one instance of the bean is created, and it's shared across the entire application context.
- Defined using @Scope("singleton") or simply @Singleton annotation.
```java
@Service
@Scope("singleton")
public class MySingletonService {
    //...
}

```

2. Prototype:
- A new instance is created each time the bean is requested.
- Defined using @Scope("prototype") or simply @Prototype annotation.
```java
@Component
@Scope("prototype")
public class MyPrototypeComponent {
    //...
}

```

3. Request:
- A new instance is created for each HTTP request in a web application.
- Used in a web-aware Spring ApplicationContext.
- Defined using @Scope("request") or simply @RequestScope annotation.

```java
@Component
@Scope("request")
public class MyRequestScopedComponent {
    //...
}

```

4. Session:
- A new instance is created for each HTTP session in a web application.
- Similar to the request scope but extends to the entire session.
- Defined using @Scope("session") or simply @SessionScope annotation.

```java
@Component
@Scope("session")
public class MySessionScopedComponent {
    //...
}
```

5. Global Session:
- Similar to the session scope, but scoped to a global HTTP session when used in a portlet context.
- Defined using @Scope("globalSession") or simply @GlobalSessionScope annotation.

```java
@Component
@Scope("globalSession")
public class MyGlobalSessionScopedComponent {
    //...
}
```

## Common Spring Bean Annotations:
1. @Component:
- Indicates that a class is a Spring component and should be managed by the Spring container.
```java
@Component
public class MyComponent {
    //...
}
```

2. @Service:
- A specialized form of @Component used to indicate that a class is a service.
```java
@Service
public class MyService {
    //...
}
```

3. @Repository:
- A specialized form of @Component used to indicate that a class is a repository.
```java
@Repository
public class MyRepository {
    //...
}
```

4. @Controller:
- A specialized form of @Component used to indicate that a class is a controller.
```java
@Controller
public class MyController {
    //...
}
```

5. @Configuration:
- Indicates that a class is a configuration class for the Spring IoC container.
```java
@Configuration
public class AppConfig {
    //...
}
```

6. @Autowired:
- Used for automatic dependency injection of beans.
```java
@Service
public class MyService {

    private final AnotherService anotherService;

    @Autowired
    public MyService(AnotherService anotherService) {
        this.anotherService = anotherService;
    }

    //...
}
```
