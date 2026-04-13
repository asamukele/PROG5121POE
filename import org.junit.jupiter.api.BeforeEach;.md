import org.junit.jupiter.api.BeforeEach;  
import org.junit.jupiter.api.Test;  
import static org.junit.jupiter.api.Assertions.*;  
  
public class LoginTest {  
  
    private Login login;  
  
    @BeforeEach  
    public void setup() {  
        login = new Login();  
    }  
  
    @Test  
    public void validUsernameTest() {  
        login.setUsername("kyl_1");  
        assertTrue(login.checkUserName());  
    }  
  
    @Test  
    public void invalidUsernameTest() {  
        login.setUsername("kyleeeeeee");  
        assertFalse(login.checkUserName());  
    }  
  
    @Test  
    public void validPasswordTest() {  
        login.setPassword("Ch&sec@ke99!");  
        assertTrue(login.checkPasswordComplexity());  
    }  
  
    @Test  
    public void invalidPasswordTest() {  
        login.setPassword("weak");  
        assertFalse(login.checkPasswordComplexity());  
    }  
  
    @Test  
    public void validPhoneTest() {  
        login.setCellPhoneNumber("+27838968976");  
        assertTrue(login.checkCellPhoneNumber());  
    }  
  
    @Test  
    public void invalidPhoneTest() {  
        login.setCellPhoneNumber("08966553");  
        assertFalse(login.checkCellPhoneNumber());  
    }  
  
    @Test  
    public void fullRegistrationSuccessTest() {  
  
        login.setFirstName("John");  
        login.setLastName("Doe");  
        login.setUsername("kyl_1");  
        login.setPassword("Ch&sec@ke99!");  
        login.setCellPhoneNumber("+27838968976");  
  
        String result = login.registerUser();  
  
        assertTrue(result.contains("Username successfully captured"));  
        assertTrue(result.contains("Password successfully captured"));  
        assertTrue(result.contains("Cell phone number successfully added"));  
    }  
  
    @Test  
    public void successfulLoginTest() {  
  
        login.setFirstName("John");  
        login.setLastName("Doe");  
        login.setUsername("kyl_1");  
        login.setPassword("Ch&sec@ke99!");  
  
        assertTrue(login.loginUser("kyl_1", "Ch&sec@ke99!"));  
    }  
  
    @Test  
    public void failedLoginTest() {  
  
        login.setUsername("kyl_1");  
        login.setPassword("Ch&sec@ke99!");  
  
        assertFalse(login.loginUser("wrong", "wrong"));  
    }  
  
    @Test  
    public void welcomeMessageTest() {  
  
        login.setFirstName("John");  
        login.setLastName("Doe");  
        login.setUsername("kyl_1");  
        login.setPassword("Ch&sec@ke99!");  
  
        String message = login.returnLoginStatus("kyl_1", "Ch&sec@ke99!");  
  
        assertEquals(  
            "Welcome John, Doe it is great to see you again.",  
            message  
        );  
    }  
}  
