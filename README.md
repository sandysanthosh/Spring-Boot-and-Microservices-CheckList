### Spring-Boot-and-Microservices-CheckList

#### Full List of Spring Boot and Microservices:

#### Spring Boot Checklist

  * Actuator: features to help you monitor and manage your application

  * JPA: to save/retrieve data

  * H2: an in-memory database

  * RestRepositories: to expose JPA repositories as REST endpoints

  * Web: Spring MVC and embedded Tomcat

  * DevTools: to auto-reload the application when files change

  * Axios: Promise-based HTTP client for JavaScript.(Test API URL in Front-end)

  * Lombok: to reduce boilerplate code

  * Hal browser-> to test the screens

  * Jaxson parser-> content management-> read data in xml/json -> Object Mapper -> Jackson API

  * Swagger ui-> springfox-swagger2 -> spring boot documentation

  * Thymeleaf - > elegient html view
 
  * EurekaDiscovery-> for service registration

  * Hystrix -> fault tolerance java library

  * Heroku -> Deploy in Cloud Application Platform


#### Spring Cloud Microservices:

      * Service Registry using Eureka

      * Client Side load balancer - Ribbon

      * Fault Tolerance - Hystrix

      * Feign Client- Easy Intergartion 

      * Router and ZUUL - Cross Cutting Concerns

      * Distributed Tracking - Sluth and Zipkin

      * Spring Cloud BUS

      * Spring Cloud Config 

#### 12FactorAPP-Microservices:

    * Codebase = One codebase tracked in revision control, many deploys - SVN

    * Dependencies = Explicitly declare and isolate dependencies - pom.xml

    * Config = Store config in the environment - DEV ,FET , ACC

    * Backing services = Treat backing services as attached resources

    * Build, release, run = Strictly separate build and run stages

    * Processes = Execute the app as one or more stateless processes

    * Port binding = Export services via port binding

    * Concurrency = Scale out via the process model

    * Disposability = Maximize robustness with fast startup and graceful shutdown

    * Dev/prod parity = Keep development, staging, and production as similar as possibe

    * Logs = Treat logs as event streams

    * Admin processes = Run admin/management tasks as one-off processes
    
#### Here is a general checklist for creating a Spring Boot application:

 * Create a new project or use an existing one.

 * Add the Spring Boot starter dependencies to the project's build file (Maven or Gradle).

 * Define the application's main class with the @SpringBootApplication annotation.

 * Create or update the application.properties or application.yml configuration file with any necessary settings.

 * Define the application's RESTful controllers with the @RestController annotation and map them to specific URLs using the @RequestMapping annotation.

 * Create any necessary service classes to handle business logic and data access.

 * Create any necessary data model classes with the @Entity annotation.

 * Configure the application to connect to a database using the spring.datasource properties in the application configuration file.

 * Create a repository interface for each of the data model classes to handle database operations.

 * Create a test class for the application and test the application's functionality using JUnit or another testing framework.

 * Build and run the application using the Spring Boot Gradle or Maven plugin, or by running the main class from an IDE.

 * Make sure to handle errors and exceptions properly and return appropriate HTTP status codes.

 * If the application will be deployed to a cloud platform, configure the necessary settings and dependencies for that platform.

 * Use Swagger or another API documentation tool to document the application's API endpoints.

 * Monitor the application's performance and make necessary adjustments to ensure optimal performance and scalability.

