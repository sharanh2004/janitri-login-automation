• Test Case ID

• Test Case Description

• Preconditions

• Test Steps

• Expected Result

• Actual Result

• Status (Pass/Fail)

Sample Test Cases

1. Test Case ID: TC001

• Description: Verify that the login button is disabled when fields are empty.

• Preconditions: User is on the login page.

• Test Steps:

1. Leave the User ID and Password fields empty.

2. Check the state of the login button.

• Expected Result: The login button should be disabled.

2. Test Case ID: TC002

• Description: Verify error message for invalid login.
• Preconditions: User is on the login page.

• Test Steps:

1. Enter random credentials in User ID and Password fields.

2. Click the login button.

• Expected Result: An error message should be displayed.

3. Test Case ID: TC003

• Description: Verify password masking functionality.

• Preconditions: User is on the login page.

• Test Steps:

1. Enter a password in the Password field.

2. Click the password visibility toggle (eye icon).

• Expected Result: The password should be visible.

4. Test Case ID: TC004

• Description: Verify presence of page elements.

• Preconditions: User is on the login page.

• Test Steps:

1. Check for the presence of User ID input field.

2. Check for the presence of Password input field.

3. Check for the presence of Login button.

4. Check for the presence of password visibility toggle.

• Expected Result: All elements should be present.

5. Test Case ID: TC005

• Description: Verify that the login button is enabled when valid credentials are entered.

• Preconditions: User is on the login page.

• Test Steps:

1. Enter valid User ID and Password.

2. Check the state of the login button.

• Expected Result: The login button should be enabled.

Task 2: Automation Code

Setting Up Your Automation Framework

1. Create a Maven Project:

• Use an IDE like IntelliJ IDEA or Eclipse.

• Create a new Maven project and add dependencies for Selenium and TestNG in your pom.xml.
<dependencies>
    <dependency>
        <groupId>org.seleniumhq.selenium</groupId>
        <artifactId>selenium-java</artifactId>
        <version>4.x.x</version>
    </dependency>
    <dependency>
        <groupId>org.testng</groupId>
        <artifactId>testng</artifactId>
        <version>7.x.x</version>
        <scope>test</scope>
    </dependency>
</dependencies>
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.annotations.AfterClass;
import org.testng.annotations.BeforeClass;

public class BaseTest {
    protected WebDriver driver;

    @BeforeClass
    public void setUp() {
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        driver = new ChromeDriver();
        driver.get("https://dev-dash.janitri.in");
    }

    @AfterClass
    public void tearDown() {
        driver.quit();
    }
}
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;

public class LoginPage {
    private WebDriver driver;

    // Locators
    private By userIdInput = By.id("userId");
    private By passwordInput = By.id("password");
    private By loginButton = By.id("loginButton");
    private By passwordToggle = By.id("passwordToggle");

    public LoginPage(WebDriver driver) {
        this.driver = driver;
    }

    public void enterUserId(String userId) {
        driver.findElement(userIdInput).sendKeys(userId);
    }

    public void enterPassword(String password) {
        driver.findElement(passwordInput).sendKeys(password);
    }

    public void clickLogin() {
        driver.findElement(loginButton).click();
    }

    public void togglePasswordVisibility() {
        driver.findElement(passwordToggle).click();
    }
}

import org.testng.annotations.Test;

public class LoginPageTest extends BaseTest {
    private LoginPage loginPage;

    @BeforeClass
    public void setUp() {
        super.setUp();
        loginPage = new LoginPage(driver);
    }

    @Test
    public void testLoginButtonDisabledWhenFieldsAreEmpty() {
        // Implement test logic
    }

    @Test
    public void testInvalidLoginShowErrorMsg() {
        // Implement test logic
    }

    @Test
    public void testPasswordMaskedButton() {
        // Implement test logic
    }
}
