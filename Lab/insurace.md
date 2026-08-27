```python
untitled3
└── src
    └── main
        └── java
            ├── base
            │   └── BaseTest.java
            ├── pages
            │   ├── HomePage.java
            │   ├── InsurancePage.java
            │   ├── PlanPage.java
            │   ├── DetailsPage.java
            │   └── ConfirmationPage.java
            └── tests
                └── InsuranceTest.java


```



## windown cmds
```python

mkdir src\main\java\base
mkdir src\main\java\pages
mkdir src\main\java\tests

type nul > src\main\java\base\BaseTest.java
type nul > src\main\java\pages\HomePage.java
type nul > src\main\java\pages\InsurancePage.java
type nul > src\main\java\pages\PlanPage.java
type nul > src\main\java\pages\DetailsPage.java
type nul > src\main\java\pages\ConfirmationPage.java
type nul > src\main\java\tests\InsuranceTest.java


```

## mac
```python

mkdir src\main\java\base
mkdir src\main\java\pages
mkdir src\main\java\tests

New-Item src\main\java\base\BaseTest.java -ItemType File
New-Item src\main\java\pages\HomePage.java -ItemType File
New-Item src\main\java\pages\InsurancePage.java -ItemType File
New-Item src\main\java\pages\PlanPage.java -ItemType File
New-Item src\main\java\pages\DetailsPage.java -ItemType File
New-Item src\main\java\pages\ConfirmationPage.java -ItemType File
New-Item src\main\java\tests\InsuranceTest.java -ItemType File



```


## BaseTest.java
```python
package base;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class BaseTest {

    protected WebDriver driver;

    public void setup() {

        driver = new ChromeDriver();

        driver.manage().window().maximize();

        driver.get(
                "file:///C:/Users/gurup/OneDrive/Documents/insurence/index.html"
        );
    }

    public void tearDown() {

        driver.quit();
    }
}



```


## pages/Homepage
```python
package pages;

import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.WebDriver;

public class HomePage {

    WebDriver driver;

    By getQuoteButton = By.className("primary-btn");

    public HomePage(WebDriver driver) {
        this.driver = driver;
    }

    public void clickGetQuote() throws InterruptedException {

        Thread.sleep(1000);

        driver.findElement(getQuoteButton).click();

        Thread.sleep(1000);
    }

    public void scrollDown() throws InterruptedException {

        ((JavascriptExecutor) driver).executeScript(
                "window.scrollTo(0, 500);"
        );

        Thread.sleep(500);
    }
}



```
