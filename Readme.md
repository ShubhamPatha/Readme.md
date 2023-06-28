
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

<!-- Headings -->   
# Usage
<!-- Code Blocks -->
``` 
  npm run start
```
<!-- Headings -->   
# Run tests
<!-- Code Blocks -->
``` 
  npm run test
```

<!-- Headings -->   
# Author
<!-- Images -->

![Markdown Logo]
(https://upload.wikimedia.org/wikipedia/commons/9/93/Google_Contacts_icon.svg)
Shubham Pathak
 <!-- UL -->
* Twitter <!-- Links -->
[@ShubhamPathak]( https://github.com/ShubhamPatha)
* Github  <!-- Links -->
[@ShubhamPathak]( https://github.com/ShubhamPatha)
<!-- Headings -->   
# Contributing
Contributions, issues an features request are welcome!
Feel free  to check issues page.


