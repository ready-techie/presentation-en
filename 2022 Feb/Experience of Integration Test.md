# Experience of Integration Test

Created: February 23, 2022
Created by: Lee Anne
Tags: TDD

[https://github.com/f-lab-edu/sago](https://github.com/f-lab-edu/sago)

# Why Integration Test?

- Curious regarding the HTTP response of the API server(Controller)
- Fast feedback for refactoring
- Software Maintenance

# Feature

- Only for nominal cases
- Auto configuration of Mock Mvc
- @TestContainers for setting auto testing environment
- **Gradle configuration**

# Code

```java
@SpringBootTest
@ActiveProfiles("test")
@Testcontainers
@AutoConfigureMockMvc
@TestInstance(TestInstance.Lifecycle.PER_CLASS)
public class UserControllerTest {

    @Autowired
    private ObjectMapper objectMapper;

    @Autowired
    private MockMvc mockMvc;

    @ClassRule
    private static final GenericContainer MY_SQL_CONTAINER = new MySQLContainer("mysql:latest")
            .withUsername("test")
            .withPassword("test")
            .withExposedPorts(3306);

    @Test
    void postLoginURI_thenReturnHttpOk() throws Exception {
        LoginDto validUser = new LoginDto();
        validUser.setNickname("sagotest18");
        validUser.setPassword("test18");
        String content = objectMapper.writeValueAsString(validUser);

        this.mockMvc.perform(post("/users/login")
                        .content(content)
                        .contentType(MediaType.APPLICATION_JSON)
                        .accept(MediaType.APPLICATION_JSON))
                .andExpect(status().isOk());
    }

    @Test
    @Transactional
    void postSignUpURI_thenReturnResponseEntity() throws Exception {
        UserDto validUser = new UserDto();

        String nickname = "pranne1224";
        String email = "melllamodahye@gmail.com";
        String password = "validtest";
        String name = "Dahye Lee";
        String phoneNumber = "010-2321-2123";
        String birth = "1999.12.25";
        String address = "Seoul";

        validUser.setNickname(nickname);
        validUser.setEmail(email);
        validUser.setPassword(password);
        validUser.setName(name);
        validUser.setPhoneNumber(phoneNumber);
        validUser.setBirth(birth);
        validUser.setAddress(address);

        String content = objectMapper.writeValueAsString(validUser);
        this.mockMvc.perform(post("/users/signUp")
                .content(content)
                .contentType(MediaType.APPLICATION_JSON)
                .accept(MediaType.APPLICATION_JSON))
                .andExpect(jsonPath("$.responseCode", Matchers.is("ACCEPTED")))
                .andExpect(jsonPath("$.data", Matchers.is("회원 등록이 완료되었습니다. 서비스 이용을 위해 이메일 인증을 해주세요.")));
    }

    @Test
    void getVerifyEmailURI_thenReturnResponseEntity() throws Exception {
        this.mockMvc.perform(get("/users/verifyEmail")
                        .param("email", "melllamodahye@gmail.com"))
                .andExpect(jsonPath("$.responseCode", Matchers.is("OK")))
                .andExpect(jsonPath("$.data", Matchers.is("회원 가입이 완료되었습니다. 로그인하여 서비스를 이용해보세요.")));
    }

    @Test
    void getCheckDuplicateIdURI_thenReturnResponseEntity() throws Exception {
        this.mockMvc.perform(get("/users/isAlreadyUsed")
                        .param("nickname", "pranne1225"))
                .andExpect(jsonPath("$.responseCode", Matchers.is("OK")))
                .andExpect(jsonPath("$.data", Matchers.is("사용 가능한 ID입니다.")));
    }
}
```
