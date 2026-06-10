```python
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.chrome.ChromeDriver;

public class hello {

    public static void main(String[] args) throws InterruptedException {

        // Launch Browser
        WebDriver driver = new ChromeDriver();

        driver.manage().window().maximize();

        // Open Website
        driver.get("https://demoqa.com/automation-practice-form");

        // Text Boxes
        driver.findElement(By.id("firstName"))
                .sendKeys("Mounesh");

        driver.findElement(By.id("lastName"))
                .sendKeys("Goud");

        driver.findElement(By.id("userEmail"))
                .sendKeys("mounesh@gmail.com");

        // Radio Button
        driver.findElement(By.xpath("//label[text()='Male']"))
                .click();

        // Mobile Number
        driver.findElement(By.id("userNumber"))
                .sendKeys("9876543210");

        // Checkbox
        driver.findElement(By.xpath("//label[text()='Sports']"))
                .click();

        // Text Area
        driver.findElement(By.id("currentAddress"))
                .sendKeys("Bangalore, Karnataka");

        // Upload File
        driver.findElement(By.id("uploadPicture"))
                .sendKeys("C:\\Users\\LENOVO\\IdeaProjects\\simpe\\screenshots\\g.jpeg");

        System.out.println("File Uploaded");

        // Submit Button
        WebElement submitBtn = driver.findElement(By.id("submit"));

        ((JavascriptExecutor) driver)
                .executeScript("arguments[0].scrollIntoView(true);", submitBtn);

        Thread.sleep(1000);

        ((JavascriptExecutor) driver)
                .executeScript("arguments[0].click();", submitBtn);

        System.out.println("Form Submitted Successfully");

        Thread.sleep(5000);

        // Close Browser
        driver.quit();
    }
}

```
