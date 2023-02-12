


Eureka is a service discovery framework for distributed systems, typically used in a microservices architecture. 

You can use Eureka to automatically register and discover services in your network. 

In a Spring Boot application, you can integrate Eureka by using the spring-cloud-starter-netflix-eureka-client dependency.

Here is an example of how to use Eureka for service registration in a Spring Boot REST API:

```

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.netflix.eureka.EnableEurekaClient;

@SpringBootApplication
@EnableEurekaClient
public class EmployeeServiceApplication {

    public static void main(String[] args) {
        SpringApplication.run(EmployeeServiceApplication.class, args);
    }
}


```

Application.properties or application.yml:


```

server.port: 8080

eureka.client.service-url.default-zone: http://localhost:8761/eureka


```

Here, the @EnableEurekaClient annotation is used to enable Eureka client support in the service.

The eureka.client.service-url.default-zone property is used to configure the URL of the Eureka server. 

When you run this service, it will automatically register itself with the Eureka server and be discoverable by other services in the network.

