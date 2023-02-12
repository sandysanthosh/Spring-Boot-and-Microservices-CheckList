

### pom.xml:

```

<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger2</artifactId>
    <version>3.0.0</version>
</dependency>

<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger-ui</artifactId>
    <version>3.0.0</version>
</dependency>


```

#### configuration class that enables Swagger UI:


```


import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

import springfox.documentation.builders.ApiInfoBuilder;
import springfox.documentation.builders.PathSelectors;
import springfox.documentation.builders.RequestHandlerSelectors;
import springfox.documentation.service.ApiInfo;
import springfox.documentation.spi.DocumentationType;
import springfox.documentation.spring.web.plugins.Docket;
import springfox.documentation.swagger2.annotations.EnableSwagger2;

@Configuration
@EnableSwagger2
public class SwaggerConfig {
    @Bean
    public Docket api() {
        return new Docket(DocumentationType.SWAGGER_2)
                .apiInfo(apiInfo())
                .select()
                .apis(RequestHandlerSelectors.basePackage("com.example.demo.controller"))
                .paths(PathSelectors.any())
                .build();
    }

    private ApiInfo apiInfo() {
        return new ApiInfoBuilder()
                .title("Employee API")
                .description("Employee API for CRUD operations")
                .version("1.0")
                .build();
    }
}


```

Run your Spring Boot application, and navigate to http://localhost:8080/swagger-ui.html to access the Swagger UI.

3.Annotate your REST controllers with Swagger annotations:

EmployeeController class that includes Swagger annotations:

```


import io.swagger.annotations.Api;
import io.swagger.annotations.ApiOperation;
import io.swagger.annotations.ApiParam;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
@RequestMapping("/api/employees")
@Api(value="Employee Management System", description="Operations pertaining to employee in Employee Management System")
public class EmployeeController {

    @Autowired
    private EmployeeService employeeService;

    @ApiOperation(value = "View a list of available employees", response = List.class)
    @GetMapping
    public List<Employee> getAllEmployees() {
        return employeeService.getAllEmployees();
    }

    @ApiOperation(value = "Get an employee by ID")
    @GetMapping("/{id}")
    public Employee getEmployeeById(
            @ApiParam(value = "Employee id from which employee object will retrieve", required = true)
            @PathVariable(value = "id") Long employeeId) {
        return employeeService.getEmployeeById(employeeId);
    }

    @ApiOperation(value = "Add an employee")
    @PostMapping
    public Employee createEmployee(
            @ApiParam(value = "Employee object store in database table", required = true)
            @RequestBody Employee employee) {
        return employeeService.createEmployee(employee);
    }

    @ApiOperation(value = "Update an employee")
    @PutMapping("/{id}")
    public Employee updateEmployee(
            @ApiParam(value = "Employee Id to update employee object", required = true)
            @PathVariable(value = "id") Long employeeId,
            @ApiParam(value = "Update employee object", required = true)
            @RequestBody Employee employee) {
        return employeeService.updateEmployee(employeeId, employee);
    }

    @ApiOperation(value = "Delete an employee")
    @DeleteMapping("/{id}")
    public void deleteEmployee(
            @ApiParam(value = "Employee Id from which employee object will delete from database table", required = true)
            @PathVariable(value = "id") Long employeeId) {
        employeeService.deleteEmployee(employeeId);
    }
}


```


