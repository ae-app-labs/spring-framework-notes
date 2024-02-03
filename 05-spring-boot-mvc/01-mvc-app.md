# Spring MVC Application
Building a simple Model-View-Controller (MVC) application involves creating a structure that separates concerns related to data (Model), user interface (View), and application logic (Controller). 

## Example Project Structure
```css
src/
└── main/
    ├── java/
    │   └── com/
    │       └── example/
    │           ├── controller/
    │           │   └── TaskController.java
    │           ├── model/
    │           │   └── Task.java
    │           └── Application.java
    └── resources/
        ├── templates/
        │   └── task.html
        └── application.properties
```

## 1. Model
```java
// Task.java
package com.example.model;

public class Task {
    private Long id;
    private String description;
    private boolean status;

    // Constructors, getters, setters
}
```
## 2. View:
- The View is responsible for presenting data to the user and receiving user input.
- Create an HTML template for displaying tasks (task.html).
```html
<!-- task.html -->
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <title>Task Details</title>
</head>
<body>
    <h2>Task Details</h2>
    <p>Description: <span th:text="${task.description}"></span></p>
    <p>Status: <span th:text="${task.status} ? 'Completed' : 'Incomplete'"></span></p>
    <form th:action="@{/tasks/complete}" method="post">
        <button type="submit">Mark as Complete</button>
    </form>
</body>
</html>
```
## 3. Controller
```java
// TaskController.java
package com.example.controller;

import com.example.model.Task;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
@RequestMapping("/tasks")
public class TaskController {
    private Task model = new Task();

    @GetMapping("/view")
    public String viewTask(Model model) {
        model.addAttribute("task", this.model);
        return "task";
    }

    @PostMapping("/complete")
    public String completeTask() {
        model.setStatus(true);
        return "redirect:/tasks/view";
    }
}
```

## Main Application
```java
// Application.java
package com.example;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

## Run Application
- Run the `Application` clas
- Navigate to http://localhost:8080/tasks/view.

