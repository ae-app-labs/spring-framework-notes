# Dependency injection and Inversion of Control (IoC)

## Without Dependency Injection

```java
// MessageService.java
public class MessageService {
    public String getMessage() {
        return "Hello, User!";
    }
}

// UserService.java
public class UserService {
    private MessageService messageService;

    public UserService() {
        this.messageService = new MessageService(); // Creating an instance here
    }

    public void processUser() {
        String message = messageService.getMessage();
        System.out.println(message);
    }
}

// MainApp.java
public class MainApp {
    public static void main(String[] args) {
        UserService userService = new UserService();
        userService.processUser();
    }
}

```

In this example:

- UserService creates an instance of MessageService within its constructor.
- UserService is responsible for creating and managing its dependencies.

## Introduction to Dependency Injection

```java
// MessageService.java (unchanged)

// UserService.java with DI
public class UserService {
    private MessageService messageService;

    public UserService(MessageService messageService) {
        this.messageService = messageService; // Injecting dependency here
    }

    public void processUser() {
        String message = messageService.getMessage();
        System.out.println(message);
    }
}

// MainApp.java
public class MainApp {
    public static void main(String[] args) {
        MessageService messageService = new MessageService();
        UserService userService = new UserService(messageService); // Injecting dependency here
        userService.processUser();
    }
}
```
In this example:

- UserService now accepts a MessageService in its constructor (constructor injection).
- The responsibility of creating and providing the MessageService instance is moved outside of UserService.

## Illustrating Inversion of Control (IoC):

```java
// MessageService.java (unchanged)

// UserService.java with IoC
public class UserService {
    private MessageService messageService;

    // IoC container (e.g., Spring) will inject the dependency here
    public void setMessageService(MessageService messageService) {
        this.messageService = messageService;
    }

    public void processUser() {
        String message = messageService.getMessage();
        System.out.println(message);
    }
}

// MainApp.java
public class MainApp {
    public static void main(String[] args) {
        MessageService messageService = new MessageService();

        UserService userService = new UserService();
        userService.setMessageService(messageService); // Injecting dependency using IoC
        userService.processUser();
    }
}
```

In this example:

- UserService no longer receives the dependency in the constructor.
- The IoC container (represented by manual injection in this case) sets the dependency using a setter method.

## Advantages
Dependency Injection promotes a more modular, testable, and maintainable codebase. It enhances flexibility, scalability, and readability, making it a valuable design pattern in software development.

