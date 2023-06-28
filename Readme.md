
# USER MANAGEMENT SYSTEM
## FRAMEWORK AND LANGUAGE USED
* JAVA 17
* MAVEN
* SPRINGBOOT 3.1.1
<!-- Headings -->   
## DATA FLOW

<!-- Code Blocks -->

  ### CONFIGURATION
  ``` 
package com.geekster.UserManagement.configuration;



import com.geekster.UserManagement.model.User;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

import java.time.LocalDate;
import java.util.ArrayList;
import java.util.List;

@Configuration
class BeanManager {

    @Bean
    public List<User> getInitializedList()
    {
        User initUser=new User(1,"Shubh",LocalDate.of(1996,12,12),"shubh@geekster.com","917042020639",LocalDate.of(2023,06,28),"09:40");

        List<User> initList = new ArrayList<>();
        initList.add(initUser);

        return initList;
    }
}
```


 ### CONTROLLER
  ``` 
package com.geekster.UserManagement.controller;

import com.geekster.UserManagement.model.User;
import com.geekster.UserManagement.service.UserService;
import jakarta.validation.Valid;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
public class UserController {

    @Autowired
    UserService userService;



    //Add user

    //Add Single user
    @PostMapping("adduser")
    String addUser(@Valid @RequestBody User user)
    {
      return userService.createUser(user);
    }
    //Add Multiple users
    @PostMapping("addusers")
    String addUsers(@Valid @RequestBody List<User> users)
    {
        return userService.createUsers(users);
    }


    //read
    // Fetch Specific user
    @GetMapping("getUser/{userId}")
    User getUser(@PathVariable Integer userId)
    {
        return userService.getUserdetail(userId);
    }
    //Fetch All user
    @GetMapping("getAllUser")
    List<User> getAllUsers()
    {
        return userService.getAllUsers();
    }




    //Update User information
    @PutMapping("updateuser/{userId}")
    String updateuser(@PathVariable Integer userId, User user)
    {
        return userService.updateuser(userId,user);
    }

    @DeleteMapping("deleteUser/{userId}")
    String removeUser(@PathVariable Integer userId)
    {
        return userService.removeUser(userId);
    }



}
```


 ### MODEL
  ``` 
package com.geekster.UserManagement.model;

import jakarta.validation.constraints.*;
import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;

import java.time.LocalDate;

@Data
@NoArgsConstructor
@AllArgsConstructor
public class User {

    @NotBlank(message = "name cannot be blank")
    private Integer userId;
    @NotBlank(message = "name cannot be blank")
    private String userName;
    @NotBlank(message = "name cannot be blank")
    private LocalDate userDOB;//EX : 2007-12-03.
    //@Email
    private String userEmail;

    @Pattern(regexp = "\\d[0-9][0-9][0-9]{10}")
    private String userContact;

    private LocalDate userDate;//EX : 2007-12-03.

    private String userTime;



}
```

### REPO
  ``` 
package com.geekster.UserManagement.repository;

import com.geekster.UserManagement.model.User;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Repository;

import java.util.List;

@Repository
public class UserRepo {

    @Autowired
    private List<User> userList;

    public List<User> getUsers() {
        return userList;
    }
}

```


### SERVICE
  ``` 
package com.geekster.UserManagement.service;

import com.geekster.UserManagement.model.User;
import com.geekster.UserManagement.repository.UserRepo;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.util.List;

@Service
public class UserService {

    @Autowired
    UserRepo userRepo;

    public List<User> getAllUsers() {
        return userRepo.getUsers();
    }

    public String createUsers(List<User> users) {
        List<User> originalList = getAllUsers();
        originalList.addAll(users);
        return "New users added";

    }

    public String createUser(User user) {
        List<User> originalList = getAllUsers();
        originalList.add(user);
        return "New user added";
    }



    public String removeUser(Integer userID) {

        List<User> originalList = getAllUsers();

        for(User user1: originalList)
        {
            if(user1.getUserId()==userID)
            {
                originalList.remove(user1);
                return "user deleted";
            }
        }

        return  "user not found";
    }




    public User getUserdetail(Integer userID) {

        List<User> originalList = getAllUsers();
User us= new User();
        for(User user1: originalList)
        {
            if(user1.getUserId()==userID)
            {


                us=user1;
            }
        }

return us;



    }





    public String updateuser(Integer userID, User user) {
        List<User> originalList = getAllUsers();

        for(User user1: originalList)
        {
            if(user1.getUserId()==userID)
            {
                user1=user;
                return "updated";
            }
        }

return "not found";
    }

}

```


### MAIN
  ``` 
package com.geekster.UserManagement;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class UserManagementApplication {

	public static void main(String[] args) {
		SpringApplication.run(UserManagementApplication.class, args);
	}

}


```





<!-- Headings -->   
# Run tests
<!-- Code Blocks -->
``` 
  npm run test
```

<!-- Headings -->   
# Author
SHUBHAM PATHAK
 <!-- UL -->
* Twitter <!-- Links -->
[@ShubhamPathak]( [https://github.com/ShubhamPatha](https://twitter.com/Shubham15022000))
* Github  <!-- Links -->
[@ShubhamPathak]( https://github.com/ShubhamPatha)
<!-- Headings -->   
# Contributing
Contributions, issues an features request are welcome!
Feel free  to check issues page.


