```python

import org.testng.Assert;
import org.testng.annotations.Test;

public class hello {

    @Test(priority = 1)
    public void testAddition() {

        int result = 10 + 20;

        Assert.assertEquals(result, 30);

        System.out.println("Addition Test Passed");
    }

    @Test(priority = 2)
    public void testSubtraction() {

        int result = 20 - 10;

        Assert.assertEquals(result, 10);

        System.out.println("Subtraction Test Passed");
    }
}

```

```python
 <dependencies>

        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>4.33.0</version>
        </dependency>

        <dependency>
            <groupId>org.testng</groupId>
            <artifactId>testng</artifactId>
            <version>7.11.0</version>
        </dependency>

    </dependencies>



```


```python

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.Assert;
import org.testng.annotations.Test;

public class SauceDemoAutomation {

    @Test
    public void completeFlow() throws InterruptedException {

        WebDriver driver = new ChromeDriver();

        driver.manage().window().maximize();

        // Open Website
        driver.get("https://www.saucedemo.com/");

        // Login
        driver.findElement(By.id("user-name"))
                .sendKeys("standard_user");

        driver.findElement(By.id("password"))
                .sendKeys("secret_sauce");

        driver.findElement(By.id("login-button"))
                .click();

        Assert.assertTrue(driver.getCurrentUrl().contains("inventory"));

        System.out.println("Login Successful");

        // Add Product
        driver.findElement(By.id("add-to-cart-sauce-labs-backpack"))
                .click();

        // Open Cart
        driver.findElement(By.className("shopping_cart_link"))
                .click();

        // Checkout
        driver.findElement(By.id("checkout"))
                .click();

        // User Details
        driver.findElement(By.id("first-name"))
                .sendKeys("Mounesh");

        driver.findElement(By.id("last-name"))
                .sendKeys("Goud");

        driver.findElement(By.id("postal-code"))
                .sendKeys("560001");

        driver.findElement(By.id("continue"))
                .click();

        // Finish Order
        driver.findElement(By.id("finish"))
                .click();

        Assert.assertTrue(
                driver.getPageSource().contains("Thank you for your order!")
        );

        System.out.println("Order Completed Successfully");

        // Back to Products
        driver.findElement(By.id("back-to-products"))
                .click();

        // Logout
        driver.findElement(By.id("react-burger-menu-btn"))
                .click();

        Thread.sleep(2000); // only to allow menu to open

        driver.findElement(By.id("logout_sidebar_link"))
                .click();

        System.out.println("Logout Successful");

        driver.quit();
    }
}

```

```python
import com.aventstack.extentreports.*;
import com.aventstack.extentreports.reporter.ExtentSparkReporter;
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;

import java.io.File;
import java.nio.file.Files;
import java.nio.file.StandardCopyOption;

public class gg {
    public static void main(String[] args) throws Exception {

        new File("reports").mkdir();  // Create reports folder

        ExtentReports extent = new ExtentReports();
        extent.attachReporter(new ExtentSparkReporter("reports/report.html"));
        ExtentTest test = extent.createTest("Google Test");

        WebDriver driver = new ChromeDriver();
        driver.get("https://www.amazon.com");

        Thread.sleep(2000);

        File src = ((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);
        Files.copy(src.toPath(),
                new File("reports/google.png").toPath(),
                StandardCopyOption.REPLACE_EXISTING);

        test.pass("Screenshot attached")
                .addScreenCaptureFromPath("google.png");

        driver.quit();
        extent.flush();

        System.out.println("Report created in reports folder");
    }
}


```

```python
 <dependency>
            <groupId>commons-io</groupId>
            <artifactId>commons-io</artifactId>
            <version>2.16.1</version>
        </dependency>

```

```python

import com.aventstack.extentreports.*;
import com.aventstack.extentreports.reporter.ExtentSparkReporter;
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;

import java.io.File;
import java.nio.file.Files;
import java.nio.file.StandardCopyOption;

public class OrangeHRMReport {

    public static void main(String[] args) throws Exception {

        // Create reports folder
        new File("reports").mkdir();

        // Extent Report
        ExtentReports extent = new ExtentReports();
        extent.attachReporter(new ExtentSparkReporter("reports/report.html"));
        ExtentTest test = extent.createTest("OrangeHRM Automation");

        // Launch Browser
        WebDriver driver = new ChromeDriver();
        driver.manage().window().maximize();

        // Open Website
        driver.get("https://opensource-demo.orangehrmlive.com/");
        test.pass("Website Opened");
        capture(driver, test, "01_HomePage");

        // Login
        driver.findElement(By.name("username")).sendKeys("Admin");
        driver.findElement(By.name("password")).sendKeys("admin123");
        driver.findElement(By.xpath("//button[@type='submit']")).click();

        Thread.sleep(3000);

        test.pass("Login Successful");
        capture(driver, test, "02_Dashboard");

        // Open PIM
        driver.findElement(By.xpath("//span[text()='PIM']")).click();
        Thread.sleep(2000);

        test.pass("PIM Opened");
        capture(driver, test, "03_PIM");

        // Open Admin
        driver.findElement(By.xpath("//span[text()='Admin']")).click();
        Thread.sleep(2000);

        test.pass("Admin Opened");
        capture(driver, test, "04_Admin");

        // Open User Menu
        driver.findElement(By.className("oxd-userdropdown-name")).click();
        Thread.sleep(1000);

        test.pass("User Menu Opened");
        capture(driver, test, "05_UserMenu");

        // Logout
        driver.findElement(By.linkText("Logout")).click();
        Thread.sleep(2000);

        test.pass("Logout Successful");
        capture(driver, test, "06_Logout");

        // Close Browser
        driver.quit();

        // Save Report
        extent.flush();

        System.out.println("Automation Completed!");
        System.out.println("Open reports/report.html");
    }

    // Screenshot Method
    public static void capture(WebDriver driver, ExtentTest test, String name) throws Exception {

        File src = ((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);

        File dest = new File("reports/" + name + ".png");

        Files.copy(src.toPath(), dest.toPath(),
                StandardCopyOption.REPLACE_EXISTING);

        test.addScreenCaptureFromPath(name + ".png");
    }
}

```

```python
import com.aventstack.extentreports.*;
import com.aventstack.extentreports.reporter.ExtentSparkReporter;
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;

import java.io.File;
import java.nio.file.Files;
import java.nio.file.StandardCopyOption;
import java.time.Duration;

public class gg {

    static ExtentTest test;
    static WebDriverWait wait;

    public static void main(String[] args) throws Exception {

        // Reports Folder
        new File("reports").mkdir();

        // Extent Report
        ExtentReports extent = new ExtentReports();
        extent.attachReporter(new ExtentSparkReporter("reports/report.html"));
        test = extent.createTest("OrangeHRM Automation");

        // Launch Browser
        WebDriver driver = new ChromeDriver();
        driver.manage().window().maximize();

        wait = new WebDriverWait(driver, Duration.ofSeconds(10));

        // Open Website
        driver.get("https://opensource-demo.orangehrmlive.com/");
        find(By.name("username"));
        test.pass("Website Opened");
        capture(driver, "01_Home");

        // Login
        find(By.name("username")).sendKeys("Admin");
        find(By.name("password")).sendKeys("admin123");
        click(By.cssSelector("button[type='submit']"));

        find(By.xpath("//h6[text()='Dashboard']"));
        test.pass("Login Successful");
        capture(driver, "02_Dashboard");

        // Open PIM
        click(By.xpath("//span[text()='PIM']"));
        find(By.xpath("//h6[text()='PIM']"));
        test.pass("PIM Opened");
        capture(driver, "03_PIM");

        // Open Admin
        click(By.xpath("//span[text()='Admin']"));
        find(By.xpath("//h6[text()='Admin']"));
        test.pass("Admin Opened");
        capture(driver, "04_Admin");

        // User Menu
        click(By.className("oxd-userdropdown-name"));
        test.pass("User Menu Opened");
        capture(driver, "05_UserMenu");

        // Logout
        click(By.linkText("Logout"));
        find(By.name("username"));
        test.pass("Logout Successful");
        capture(driver, "06_Logout");

        // Close Browser
        driver.quit();

        // Save Report
        extent.flush();

        System.out.println("Automation Completed!");
        System.out.println("Open reports/report.html");
    }

    // Wait for element and return it
    public static WebElement find(By by) {
        return wait.until(ExpectedConditions.visibilityOfElementLocated(by));
    }

    // Wait and click
    public static void click(By by) {
        wait.until(ExpectedConditions.elementToBeClickable(by)).click();
    }

    // Screenshot
    public static void capture(WebDriver driver, String name) throws Exception {

        File src = ((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);

        File dest = new File("reports/" + name + ".png");

        Files.copy(src.toPath(), dest.toPath(),
                StandardCopyOption.REPLACE_EXISTING);

        test.addScreenCaptureFromPath(name + ".png");
    }
}


```
