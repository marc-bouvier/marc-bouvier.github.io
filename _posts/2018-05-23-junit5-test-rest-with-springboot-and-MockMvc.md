In order to run tests of REST Api with a minimal Spring context in Junit5.
BDD Mockito style.

## Light test configuration
```
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration;
import org.springframework.boot.autoconfigure.orm.jpa.HibernateJpaAutoConfiguration;
import org.springframework.boot.builder.SpringApplicationBuilder;
import org.springframework.context.annotation.ComponentScan;

/**
 * Light Spring context to test only REST.
 */
@SpringBootApplication(exclude = {DataSourceAutoConfiguration.class, HibernateJpaAutoConfiguration.class})
@ComponentScan({"com.adis.g2a.gestion.acte.rest"})
public class MyRestTestConfig {

    public static void main(String[] args) {
        new SpringApplicationBuilder(MyRestTestConfig.class).run(args);
    }
}

```

## Test class
```
//...
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.web.servlet.WebMvcTest;
import org.springframework.boot.test.mock.mockito.MockBean;
import org.springframework.test.context.junit.jupiter.web.SpringJUnitWebConfig;
import org.springframework.test.web.servlet.MockMvc;

import static org.mockito.BDDMockito.willThrow;
import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.post;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.status;

@WebMvcTest(value = MyResourceRestController.class, secure = false)
@SpringJUnitWebConfig(MyRestTestConfig.class)
class MyResourceRestTest {

    @Autowired
    private MockMvc mvc;
    
    @MockBean
    private SomeInjectedService someInjectedService;
    

    @Test
    void updateResource() throws Exception {

        mvc.perform(post("/api/myresource/{resourceId}/param/{param}",
                1L, "paramValue"))
                .andExpect(status().isOk());
    }
}
```

## Source

* [Spring official documentation](https://docs.spring.io/spring-boot/docs/current/reference/html/boot-features-testing.html#boot-features-testing-spring-boot-applications-testing-autoconfigured-mvc-tests)
