# Setting up Spring Boot

## Prerequisites
- Java SDK
- IDE like VS Code, Intellij Idea or Eclipse
- Maven or Gradle

## Create a New Spring Boot Project
1. Using Spring Initializer:
- Go to Spring [Initializer](https://start.spring.io/).
- Select your project settings (e.g., Maven or Gradle, Java version, packaging, etc.).
- Add dependencies (e.g., "Spring Web" for a basic web application).
- Click "Generate" to download a ZIP file containing your project.

2. Using IDE:
- If you're using an IDE like IntelliJ or Eclipse, you can use their built-in project creation tools.
- In IntelliJ IDEA, go to File -> New -> Project, select "Spring Initializer" as the project type, and follow the wizard.

## Create Your First Controller
1. Create a new `java` class `HelloController.java`
```java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {

    @GetMapping("/hello")
    public String hello() {
        return "Hello, Spring Boot!";
    }
}
```
2. Access the endpoint
Restart the application (if already running) and navigate to [http://localhost:8080/hello](http://localhost:8080/hello)

## spring-boot-starter
The spring-boot-starter is a parent starter that provides common dependencies used across different Spring Boot projects. It helps maintain consistency and reduces the effort needed for dependency management.
1. Spring MVC (Model-View-Controller):
- Spring MVC is a framework for building web applications. It provides a model-view-controller architecture that simplifies the development of robust and scalable web applications.
2. Embedded Web Server (Tomcat, Jetty, or Undertow):
- Spring Boot includes an embedded web server (Tomcat, Jetty, or Undertow) so that you can run your web application as a standalone JAR or WAR file without needing to deploy it to a separate server.
3. Spring Boot Auto-Configuration for Web:
- Spring Boot provides auto-configuration to set up the web application environment based on best practices. It automatically configures components like DispatcherServlet, RequestMappingHandlerMapping, and others.
4. Spring Boot DevTools:
- DevTools is an optional dependency included in the spring-boot-starter-web that provides additional development-time features, such as automatic application restart, live reloading, and enhanced debugging.
5. Validation API:
- The Java Validation API is included for handling validation of data, especially in the context of form submissions in web applications.
6. Common Logging:
- Spring Boot uses common logging for its logging needs. This is configured to be compatible with various logging frameworks like Logback, Log4j, etc.