# first-project-java-spring
## Built With

This project was generated with https://start.spring.io/ and use: 
* Project: Maven
* Language: Java 23
* Dependencies: Spring Web, Lombok, Thymeleaf

## Case Study

### Scenario

a lecturer at Vistula University asked students to create a simple web application that:

* Will use Spring Framework
* there will be a controller in the code
* In frontend there will be text and image

### Purpose

* creating a new project from scratch using Spring Boot,
* writing the first Spring controller,
* launching the project and sending an HTTP request,
* using (with understanding) annotations @ResponseBody
* Demonstrate the use of Spring Boot to build a web application.
* To demonstrate Thymeleaf capabilities in rendering dynamic views.
* Create suitable readme.md with case study

## Launch Project

### Requirements

* Language Java 17 or latest
* Maven (or other build system that supoorts Spring Boot )
* IDE (np. IntelliJ IDEA)

### Steps 

1. Clone the project or copy files to your environment.
2. Open project int IDE.
3. Run class "FirstProjectJavaSpringApplication"
4. Open your browser and go to the following addresses:
   * "http://localhost:8080/greeting?name=Vistula" - shows frontend view with text.

## Usage

This project was created on the basis of a tutorial and should show how to create a simple application using the Spring framework.
The following example shows the use of:

### 1.Main class

File path: src/main/java/pl/edu/vistula/first_project_java_spring/FirstProjectJavaSpringApplication.java

This class acts as the start point for the application and starts the Spring Boot server.

````java
package pl.edu.vistula.first_project_java_spring;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class FirstProjectJavaSpringApplication {

   public static void main(String[] args) {
      SpringApplication.run(FirstProjectJavaSpringApplication.class, args);
   }

}
````
* @SpringBootApplication Automatically configures app and scans components in a package and subpackages.

### 2.Controler

File path: src/main/java/pl/edu/vistula/first_project_java_spring/controller/HelloController.java

The controller supports two endpoints:
* "/" – returns simple text.
* "/greeting" – generates a dynamic view with the possibility of passing the name parameter.

````java
package pl.edu.vistula.first_project_java_spring.controller;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@Controller
//@RestController

public class HelloController {

    @GetMapping(value = "/")
    public String hello() { return "Hello Vistula, in my first Spring controller."; }

    @GetMapping("/greeting")
    public String greeting(@RequestParam(name = "name", required = false, defaultValue ="World") String name, Model model) {
        model.addAttribute("name", name);
        return "greeting";

    }
    //http://localhost:8080/greeting?name=Vistula
}
````
* Endpoint "/" :
  * It returns a simple text: "Hello Vistula, in my first Spring controller.".
* Endpoint "/greeting" :
  *  Expects a name parameter in the URL (e.g., http://localhost:8080/greeting?name=Vistula).
  *  Passes the parameter value to the model (model.addAttribute("name", name)).
     Generates a view greeting.html.

### 3. Frontend / View

File path: src/main/resources/templates/greeting.html

A view rendered with Thymeleaf that displays a greeting and loads an image.

````html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <title>Getting Started: Serving Web Content</title>
    <meta http-equiv="Content-Type" content="text/html" charset="UTF-8" />
</head>
<body>
    <p th:text="'Hello, ' + ${name} + '!' "/>
<p>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
</p>
<img th:src="@{/livery_16x9_4-1.png}" width="1000" height="600" />
</body>
</html>
````
* Displays the greeting based on the name parameter.
* Renders a static livery_16x9_4-1.png image from the resources/static directory.

And working example looks like this:
<div align="center">
<a>
<img src="images/Zrzut1.png" alt="Page" />
</a>
</div>

## Further Help

To get more help on projects created with framework Spring check: https://docs.spring.io/initializr/docs/current-SNAPSHOT/reference/html/ 