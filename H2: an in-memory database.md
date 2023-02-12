```

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import javax.persistence.*;
import java.util.List;

@RestController
@RequestMapping("/api/products")
public class ProductController {

  @Autowired
  private ProductRepository repository;

  @GetMapping
  public List<Product> getAllProducts() {
    return repository.findAll();
  }

  @PostMapping
  public Product addProduct(@RequestBody Product product) {
    return repository.save(product);
  }

  @PutMapping("/{id}")
  public Product updateProduct(@PathVariable long id, @RequestBody Product product) {
    product.setId(id);
    return repository.save(product);
  }

  @DeleteMapping("/{id}")
  public void deleteProduct(@PathVariable long id) {
    repository.deleteById(id);
  }
}

@Entity
class Product {

  @Id
  @GeneratedValue(strategy=GenerationType.AUTO)
  private long id;

  private String name;
  private double price;

  public long getId() {
    return id;
  }

  public void setId(long id) {
    this.id = id;
  }

  public String getName() {
    return name;
  }

  public void setName(String name) {
    this.name = name;
  }

  public double getPrice() {
    return price;
  }

  public void setPrice(double price) {
    this.price = price;
  }
}

interface ProductRepository extends JpaRepository<Product, Long> {

}


```


Here is an example of how to create a Spring Boot API using H2 as the database:

typescript
Copy code
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import javax.persistence.*;
import java.util.List;

@RestController
@RequestMapping("/api/products")
public class ProductController {

  @Autowired
  private ProductRepository repository;

  @GetMapping
  public List<Product> getAllProducts() {
    return repository.findAll();
  }

  @PostMapping
  public Product addProduct(@RequestBody Product product) {
    return repository.save(product);
  }

  @PutMapping("/{id}")
  public Product updateProduct(@PathVariable long id, @RequestBody Product product) {
    product.setId(id);
    return repository.save(product);
  }

  @DeleteMapping("/{id}")
  public void deleteProduct(@PathVariable long id) {
    repository.deleteById(id);
  }
}

@Entity
class Product {

  @Id
  @GeneratedValue(strategy=GenerationType.AUTO)
  private long id;

  private String name;
  private double price;

  public long getId() {
    return id;
  }

  public void setId(long id) {
    this.id = id;
  }

  public String getName() {
    return name;
  }

  public void setName(String name) {
    this.name = name;
  }

  public double getPrice() {
    return price;
  }

  public void setPrice(double price) {
    this.price = price;
  }
}

interface ProductRepository extends JpaRepository<Product, Long> {

}
In this example, we have a ProductController that defines the REST endpoints for creating, reading, updating, and deleting products.
  
  The Product entity represents a product and has properties for the id, name, and price. 
  
  The ProductRepository is an interface that extends JpaRepository and provides basic CRUD operations for the Product entity.

  The @Autowired annotation is used to inject an instance of ProductRepository into the ProductController. 
  
  The @RestController annotation indicates that this class is a REST controller, and the @RequestMapping annotation maps the endpoint to /api/products.

  The getAllProducts method maps to the GET /api/products endpoint and returns a list of all products. 
  
  The addProduct method maps to the POST /api/products endpoint and adds a new product to the repository. 
  
  The updateProduct method maps to the PUT /api/products/{id} endpoint and updates an existing product. 
  
  The deleteProduct method maps to the DELETE /api/products/{id} endpoint and deletes a product from the repository.


  #### In order to use H2 as the database, you will need to add the following dependency to your pom.xml file:


  
  ```
  
  <dependency>
  <groupId>com.h2database</groupId>

   ```
    
    #### Application.properties:
    
    ```
    
# H2 Configuration
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

# Datasource Configuration
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=password

# JPA Configuration
spring.jpa.show-sql=true
spring.jpa.hibernate.ddl-auto=create-drop
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.H2Dialect

    
    ```


    The spring.h2.console.enabled and spring.h2.console.path properties enable the H2 web console, which can be used to view and manage the in-memory H2 database.

    The spring.datasource properties configure the datasource for the H2 database. 
    
    The url property specifies the URL for the H2 database, which is jdbc:h2:mem:testdb for an in-memory database. 
    
    The driverClassName property specifies the H2 driver class, which is org.h2.Driver. 
    
    The username and password properties specify the credentials for connecting to the database.

    The spring.jpa properties configure JPA for the application. 
    
    The show-sql property sets the value to true, which will cause Hibernate to log the SQL statements to the console. 
    
    The ddl-auto property is set to create-drop, which will cause Hibernate to automatically create the schema and drop it when the application shuts down. 
    
    The hibernate.dialect property is set to org.hibernate.dialect.H2Dialect, which specifies the H2 dialect for Hibernate.
    
    

  
  
