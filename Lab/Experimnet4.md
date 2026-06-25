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
