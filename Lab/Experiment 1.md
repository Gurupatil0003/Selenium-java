```python
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class LoginAutomation {

    public static void main(String[] args) {

        // Launch Chrome Browser
        WebDriver driver = new ChromeDriver();

        // Open Website
        driver.get("https://practicetestautomation.com/practice-test-login/");

        // Maximize Window
        driver.manage().window().maximize();

        // Enter Username
        WebElement username =
                driver.findElement(By.id("username"));
        username.sendKeys("student");

        // Enter Password
        WebElement password =
                driver.findElement(By.id("password"));
        password.sendKeys("Password123");

        // Click Login Button
        WebElement loginBtn =
                driver.findElement(By.id("submit"));
        loginBtn.click();

        // Verify Login
        String title = driver.getTitle();
        System.out.println("Page Title: " + title);

        // Close Browser
        driver.quit();
    }
}


```
