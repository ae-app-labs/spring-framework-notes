# Spring Beans
A "bean" is an object that is created, managed, and configured by the Spring IoC (Inversion of Control) container. Beans are the fundamental building blocks of a Spring application. They are Java objects that form the backbone of the application and are managed by the Spring container.

## Key Characteristics of Spring Beans:
### Java Objects:

- Beans are essentially Java objects created from regular Java classes.

### Managed by the Spring Container:
- The Spring IoC container is responsible for instantiating, configuring, and managing the lifecycle of beans.

### Configurable:
- Beans are typically configured in the Spring configuration files (XML, JavaConfig, or annotations).

### Singleton or Prototype:
- Beans can be configured as singletons (a single instance shared by multiple parts of the application) or prototypes (a new instance created each time).

## Lifecycle of a Spring Bean:
The lifecycle of a Spring bean consists of several stages:

1. Instantiation:
- The bean is created. This can happen through constructor invocation or a factory method.
2. Populating Properties:
- The container sets the properties and dependencies of the bean. This is often done through setters or fields.
3. Bean Post-Processing:
- If there are any BeanPostProcessors configured, they can process the bean before and after initialization.

4. Initialization:
- If the bean implements the InitializingBean interface, the afterPropertiesSet method is invoked. Alternatively, the bean can define an initialization method using the init-method attribute in XML configuration or @PostConstruct annotation.

5. In Use:
- The bean is now ready for use by the application.
6. Destruction:
- If the bean implements the DisposableBean interface, the destroy method is called during the container shutdown. Alternatively, the bean can define a destruction method using the destroy-method attribute in XML configuration or @PreDestroy annotation.