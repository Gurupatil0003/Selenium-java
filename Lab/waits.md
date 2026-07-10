## Implit and Explit wait
```python
import java.time.Duration;
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;

public class ExplicitWaitDemo {

    public static void main(String[] args) {

        WebDriver driver = new ChromeDriver();

        driver.manage().window().maximize();

        driver.get("https://the-internet.herokuapp.com/dynamic_loading/1");

        driver.findElement(By.xpath("//button[text()='Start']")).click();

        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));

        WebElement text = wait.until(
                ExpectedConditions.visibilityOfElementLocated(By.id("finish"))
        );

        System.out.println(text.getText());

        driver.quit();
    }
}

```

```python

import java.time.Duration;
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;

public class ImplicitWaitDemo {

    public static void main(String[] args) {

        WebDriver driver = new ChromeDriver();

        // Implicit Wait
        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));

        driver.manage().window().maximize();

        driver.get("https://the-internet.herokuapp.com/dynamic_loading/1");

        driver.findElement(By.xpath("//button[text()='Start']")).click();

        // Selenium waits up to 10 seconds if the element is not immediately found
        WebElement text = driver.findElement(By.id("finish"));

        System.out.println(text.getText());

        driver.quit();
    }
}

```

## Alert
```python
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;

public class g {

    public static void main(String[] args) throws Exception{

        WebDriver driver = new ChromeDriver();

        driver.manage().window().maximize();
        driver.get("https://the-internet.herokuapp.com/javascript_alerts");

        // Simple Alert
        driver.findElement(By.xpath("//button[text()='Click for JS Alert']")).click();
        Thread.sleep(2000);
        driver.switchTo().alert().accept();
        Thread.sleep(2000);



        // Confirmation Alert
        driver.findElement(By.xpath("//button[text()='Click for JS Confirm']")).click();
        Thread.sleep(2000);

        driver.switchTo().alert().dismiss();
        Thread.sleep(2000);

        // Prompt Alert
        driver.findElement(By.xpath("//button[text()='Click for JS Prompt']")).click();
        Thread.sleep(2000);

        Alert alert = driver.switchTo().alert();
        Thread.sleep(2000);

        alert.sendKeys("Hello");
        Thread.sleep(2000);

        alert.accept();

        driver.quit();
    }
}


```
