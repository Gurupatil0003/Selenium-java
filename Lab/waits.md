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

```python
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class g {

    public static void main(String[] args) throws Exception {

        WebDriver driver = new ChromeDriver();

        driver.manage().window().maximize();

        driver.get("https://demo.automationtesting.in/Frames.html");

        // Locate the iframe
        WebElement frame = driver.findElement(By.id("singleframe"));

        // Switch to iframe
        driver.switchTo().frame(frame);

        // Type inside the textbox
        driver.findElement(By.xpath("//input[@type='text']"))
                .sendKeys("Hello Selenium");

        Thread.sleep(3000);

        // Back to main page
        driver.switchTo().defaultContent();

        System.out.println(driver.getTitle());

        Thread.sleep(2000);

        driver.quit();
    }
}


```

## table
```python
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;
import java.util.List;

public class g {

    public static void main(String[] args) {

        WebDriver driver = new ChromeDriver();

        driver.get("https://the-internet.herokuapp.com/tables");
        driver.manage().window().maximize();

        WebElement table = driver.findElement(By.id("table1"));

        List<WebElement> rows = table.findElements(By.xpath(".//tbody/tr"));

        for (int i = 1; i <= rows.size(); i++) {

            List<WebElement> cols = table.findElements(
                    By.xpath(".//tbody/tr[" + i + "]/td"));

            for (int j = 1; j <= cols.size(); j++) {

                String value = table.findElement(
                                By.xpath(".//tbody/tr[" + i + "]/td[" + j + "]"))
                        .getText();

                System.out.print(value + "\t");
            }

            System.out.println();
        }

        driver.quit();
    }
}

```
## waits
```python

import java.time.Duration;
import java.util.List;

import org.openqa.selenium.By;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;

public class hello {

    public static void main(String[] args) {

        ChromeDriver driver = new ChromeDriver();

        driver.manage().window().maximize();
        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));

        driver.get("https://demo.automationtesting.in/Dynamic.html");

        // Get all draggable images
        List<WebElement> images = driver.findElements(By.xpath("//img"));

        // Get drop area
        WebElement dropArea = driver.findElement(By.id("droparea"));

        // Actions class
        Actions act = new Actions(driver);

        // Drag each image
        for (WebElement image : images) {

            act.dragAndDrop(image, dropArea).perform();
        }

        driver.quit();
    }
}

```

```python

import java.time.Duration;
import java.util.List;

import org.openqa.selenium.By;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;

public class hello {

    public static void main(String[] args) {

        ChromeDriver driver = new ChromeDriver();

        driver.manage().window().maximize();

        driver.get("https://demo.automationtesting.in/Dynamic.html");

        // Explicit Wait
        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));

        // Wait until the drop area is visible
        WebElement dropArea = wait.until(
                ExpectedConditions.visibilityOfElementLocated(By.id("droparea")));

        // Wait until all images are visible
        List<WebElement> images = wait.until(
                ExpectedConditions.visibilityOfAllElementsLocatedBy(By.xpath("//img")));

        Actions act = new Actions(driver);

        for (WebElement image : images) {
            act.dragAndDrop(image, dropArea).perform();
        }

        driver.quit();
    }
}
```
