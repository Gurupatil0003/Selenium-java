```python
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.Select;

public class gg {

    public static void main(String[] args) throws InterruptedException {

        // Launch Browser
        WebDriver driver = new ChromeDriver();
        driver.manage().window().maximize();

        // Open Website
        driver.get("https://demoqa.com/automation-practice-form");

        // First Name
        driver.findElement(By.id("firstName"))
                .sendKeys("Mounesh");

        // Last Name
        driver.findElement(By.id("lastName"))
                .sendKeys("Goud");

        // Email
        driver.findElement(By.id("userEmail"))
                .sendKeys("mounesh@gmail.com");

        // Gender
        driver.findElement(By.xpath("//label[text()='Male']"))
                .click();

        // Mobile Number
        driver.findElement(By.id("userNumber"))
                .sendKeys("9876543210");

        // Hobbies
        driver.findElement(By.xpath("//label[text()='Sports']"))
                .click();

        // Upload Picture
        driver.findElement(By.id("uploadPicture"))
                .sendKeys("C:\\Users\\LENOVO\\IdeaProjects\\simpe\\screenshots\\g.jpeg");

        // Address
        driver.findElement(By.id("currentAddress"))
                .sendKeys("Bangalore, Karnataka");

        // Simple Scroll Down
        ((JavascriptExecutor) driver)
                .executeScript("window.scrollBy(0,500)");

        Thread.sleep(1000);

        // Submit
        driver.findElement(By.id("submit"))
                .click();

        System.out.println("Form Submitted Successfully");

        Thread.sleep(5000);

        // Close Browser
        driver.quit();
    }
}
```

```python

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.Select;

public class gg {

    public static void main(String[] args) throws InterruptedException {

        // Launch Browser
        WebDriver driver = new ChromeDriver();
        driver.manage().window().maximize();

        // Open Website
        driver.get("https://demoqa.com/automation-practice-form");

        // First Name
        driver.findElement(By.id("firstName"))
                .sendKeys("Mounesh");

        // Last Name
        driver.findElement(By.id("lastName"))
                .sendKeys("Goud");

        // Email
        driver.findElement(By.id("userEmail"))
                .sendKeys("mounesh@gmail.com");

        // Gender
        driver.findElement(By.xpath("//label[text()='Male']"))
                .click();

        // Mobile Number
        driver.findElement(By.id("userNumber"))
                .sendKeys("9876543210");

        // Date of Birth
        driver.findElement(By.id("dateOfBirthInput"))
                .click();

        Select month = new Select(
                driver.findElement(By.className("react-datepicker__month-select")));
        month.selectByVisibleText("May");

        Select year = new Select(
                driver.findElement(By.className("react-datepicker__year-select")));
        year.selectByVisibleText("1998");

        driver.findElement(By.xpath("//div[text()='15']"))
                .click();

        // Subject
        driver.findElement(By.id("subjectsInput"))
                .sendKeys("Maths");
        driver.findElement(By.id("subjectsInput"))
                .sendKeys("\n");

        // Hobbies
        driver.findElement(By.xpath("//label[text()='Sports']"))
                .click();

        // Upload Picture
        driver.findElement(By.id("uploadPicture"))
                .sendKeys("C:\\Users\\LENOVO\\IdeaProjects\\simpe\\screenshots\\g.jpeg");

        // Address
        driver.findElement(By.id("currentAddress"))
                .sendKeys("Bangalore, Karnataka");

        // Simple Scroll Down
        ((JavascriptExecutor) driver)
                .executeScript("window.scrollBy(0,500)");

        Thread.sleep(1000);

        // State
        driver.findElement(By.id("react-select-3-input"))
                .sendKeys("NCR");
        driver.findElement(By.id("react-select-3-input"))
                .sendKeys("\n");

        Thread.sleep(1000);

        // City
        driver.findElement(By.id("react-select-4-input"))
                .sendKeys("Delhi");
        driver.findElement(By.id("react-select-4-input"))
                .sendKeys("\n");

        Thread.sleep(1000);

        // Submit
        driver.findElement(By.id("submit"))
                .click();

        System.out.println("Form Submitted Successfully");

        Thread.sleep(5000);

        // Close Browser
        driver.quit();
    }
}

```
