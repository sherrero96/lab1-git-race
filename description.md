# Table of Contents

1. [How to build the code](#how-to-build-the-code)
2. [How to test the code](#how-to-test-the-code)
3. [How to deploy the code in a server](#how-to-deploy-the-code-in-a-server)
4. [Which are the technologies used in the code](#which-are-the-technologies-used-in-the-code)
5. [How these technologies work](#how-these-technologies-work)
6. [What means each a specific piece or code](#what-means-each-a-specific-piece-or-code)
7. [Which is the purpose of a specific Java annotation](#which-is-the-purpose-of-a-specific-java-annotation)

## How to build the code

This application uses [Gradle](http://gradle.org) to build the code. Please, refer to the [Gradle user guide](https://docs.gradle.org/current/userguide/installation.html) for its installation. Once it is installed just do:

```bash
cd lab1-git-race
gradle build
```

After a few seconds, "BUILD SUCCESSFUL" indicates that the build has completed. There you’ll find generated WAR file inside *libs* folder under *build* directory.

## How to test the code

Testing the code can be done automatically by using the JUint library for unit tests. Integration tests may also use specific components of the Spring framework to help with this task.

Project is tested upon each build. However, running all the tests can be requested manually, just do:

```bash
cd lab1-git-race
gradle check
```

In order to run unit test only, use instead:

```bash
cd lab1-git-race
gradle test
```

## How to deploy the code in a server

For developing stages of the project, it is possible to run a *ad-hoc* Tomcat server, just do:

```bash
cd lab1-git-race
gradle bootRun
```
Refer to [Apache Tomcat documentation](https://tomcat.apache.org/tomcat-8.0-doc/deployer-howto.html) about how to deploy a WAR file, once [deliverables have been built](#how-to-build-the-code).

## Which are the technologies used in the code

## How these technologies work

### Junit4

JUnit is one of the most popular testing frameworks for Java. Although JUnit5 is the newest version of the framework, JUnit4 is still used in many projects. Let's see [how it works](#how-junit4-works).

### Spring

Spring Boot makes it easy to create stand-alone, production-grade Spring based Applications that you can "just run".

We take an opinionated view of the Spring platform and third-party libraries so you can get started with minimum fuss. Most Spring Boot applications need very little Spring configuration.

In fact, a professor of Web Engineering demonstrated how to mount URL Shortener in less than 5 minutes with Spring Boot.

#### Some advantages over using spring

* It is very easy to develop Spring Based applications with Java or Groovy.
* It reduces lots of development time and increases productivity.
* It provides Embedded HTTP servers like Tomcat, Jetty etc. to develop and test our web applications very easily.
* It provides CLI (Command Line Interface) tool to develop and test Spring Boot(Java or Groovy) Applications from command prompt very easily and quickly.
* And much more.

The sources used and where much more information can be found:
* [spring.io](https://spring.io/projects/spring-boot)
* [hwww.journaldev.com/7969/spring-boot-tutorial](https://www.journaldev.com/7969/spring-boot-tutorial)
  
## How these technologies work

### How Junit4 works

Creating a test with JUnit4 is really easy. In order to do it follow these steps:

1. Create the class you want to test (e.g. JavaClass.java).
2. Create a class for testing (e.g. JavaClassTest.java).
3. For each test you want to create, write a method with @Test tag above.
4. Run the test.

> **Note:** You may to import some JUnit4 libraries.

For further information, you can visit <https://github.com/junit-team/junit4/wiki/Getting-started>.

### To start a project with Spring boot

#### Prerequisites
1. We are going to use the gradle tool, so it must be installed.

#### Create Spring Boot proyect

1. Create gradle proyect

    ```bash
    gradle init
    ```

    Let's select the desired options, using java as language.

1. Transform into a Spring Boot Web application
    Edit the class App at src/... and adds the following imports:

    ```java
    import org.springframework.boot.SpringApplication;
    import org.springframework.boot.autoconfigure.SpringBootApplication;
    ```

    Above the definition of the App function adds : @SpringBootApplication
    And finally, within the main function write `SpringApplication.run(App.class, args);`

1. Editing the gradle builder
    Add the following plugins and dependencies:

    ```java
    id 'org.springframework.boot' version '2.1.8.RELEASE'
    id 'io.spring.dependency-management' version '1.0.8.RELEASE'

    implementation 'org.springframework.boot:spring-boot-starter-web'
    ```

1. This is the initial application of Spring Boot.

1. Now you can add the actions that are triggered when making requests to endpoints.

## What means each a specific piece or code

## Which is the purpose of a specific Java annotation

### @Controller

As spring boot it follows the architecture Model-View-Controller, @Controller annotation indicates that the annotated class is a controller. It is a specialization of @Component and is autodetected through classpath scanning. It is typically used in combination with annotated handler methods based on the @RequestMapping annotation.
In short, it serves to indicate that it is the controller class of the architecture.

### @Value

To talk about the @Value annotation, first we must talk about the spring boot properties file.
Property files are used to keep a number of properties in a single file to run the application in any environment. In Spring Boot, the properties file is stored in the application.properties file.
The syntax of the properties file is

```bash
app.{"key"}="value"
```

The @Value annotation is used to read the value of some of the properties stored in the properties file.
In this file, you can see data about the environment, about values or variables or even properties of the application as the listening port.
The syntax of the @Value annotation is

```java
@Value("${property_key_name}")
```


### @GetMapping("/")

@GetMapping annotation maps HTTP GET requests onto specific handler methods. It is a composed annotation that acts as a shortcut for @RequestMapping(method = RequestMethod.GET).
If the argument is "/", it means that the method whose annotation is @GetMapping("/") will be triggered when a request is made to the "root" of the web.
If the argument is of the type "string/string...etc", it means that the method whose annotation is @GetMapping("string/string...") will be triggered when a request is made to this endpoint of the web.



