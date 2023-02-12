```

import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class UserController {

    @GetMapping("/users")
    public User getUser() {
        return new User("John", "Doe");
    }

}

@Data
@NoArgsConstructor
@AllArgsConstructor
class User {
    private String firstName;
    private String lastName;
}


```

In this example, we have a UserController class that has a GET endpoint /users which returns a User object. 

The User class uses Lombok's @Data annotation, which generates the getters, setters, equals, hashCode, and toString methods for us.

The @NoArgsConstructor and @AllArgsConstructor annotations generate a no-arg constructor and a constructor with all arguments, respectively.

