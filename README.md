# Hosting a Simple Web Page in Ubuntu VM (NAT Network Demo)


```python
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.Assert;
import org.testng.annotations.Test;

public class AddButtonTest {

    @Test
    public void verifyButtonCreation() {

        WebDriver driver = new ChromeDriver();

        driver.manage().window().maximize();

        driver.get("https://the-internet.herokuapp.com/add_remove_elements/");

        // Click Add Element button
        driver.findElement(By.xpath("//button[text()='Add Element']"))
                .click();

        // Verify Delete button appears
        boolean isDisplayed =
                driver.findElement(By.xpath("//button[text()='Delete']"))
                        .isDisplayed();

        Assert.assertTrue(isDisplayed);

        System.out.println("Delete button displayed successfully");

        driver.quit();
    }
}

```
## Step 1: Start Ubuntu

Open Terminal and install Python (if not already installed):

```bash
sudo apt update
sudo apt install python3
```

## Step 2: Create a Web Page

- Create a file:
```python
nano index.html
```
- Write the following content:
```python
<h1>Hello from Ubuntu VM!</h1>
<h2>NAT Network Demo</h2>
```

#### Step 3: Start a Web Server
```python
Run:

python3 -m http.server 8000
```
```python
You'll see:

Serving HTTP on 0.0.0.0 port 8000 ...

This means Ubuntu is hosting a website.

```
### Step 4: Open Firefox Inside Ubuntu
```python
Go to:

http://localhost:8000

You'll see:

Hello from Ubuntu VM!
NAT Network Demo

Success! 🎉

What's Happening?
Windows 11
     |
VirtualBox
     |
Ubuntu VM
     |
Web Server (Port 8000)

The website is running inside Ubuntu.
```
#### Step 5: Try Accessing It from Windows

```python
First, find Ubuntu's IP address:

ip a

You'll see something like:

10.0.2.15

Now on Windows, open Chrome and try:

http://10.0.2.15:8000
Most Likely Result
❌ It won't open.
```

```python
import org.apache.logging.log4j.LogManager;
import org.apache.logging.log4j.Logger;

public class TestLogging {

    private static final Logger logger = LogManager.getLogger(TestLogging.class);

    public static void main(String[] args) {
        logger.info("Application started.");
        logger.debug("Debug message.");
        logger.warn("Warning message.");
        logger.error("Error message.");
        logger.fatal("Fatal message.");
    }
}


```

```python
import org.apache.logging.log4j.LogManager;
import org.apache.logging.log4j.Logger;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class SeleniumWebsiteAutomation {

    private static final Logger logger = LogManager.getLogger(SeleniumWebsiteAutomation.class);

    public static void main(String[] args) {

        logger.trace("Automation started.");
        logger.debug("Launching Chrome browser.");

        WebDriver driver = new ChromeDriver();

        logger.info("Opening Selenium website.");
        driver.get("https://www.selenium.dev");

        logger.info("Clicking Downloads menu.");
        driver.findElement(By.linkText("Downloads")).click();

        logger.info("Page Title: " + driver.getTitle());

        driver.quit();

        logger.info("Browser closed.");
    }
}

```
