# 🚌 Bus Booking Automation Framework

This project demonstrates a **Hybrid Selenium Automation Framework** using **Java, Maven, TestNG, and Page Object Model (POM)** to automate a bus booking application.

---

## 📥 Download Source Code

Click below to download the original bus booking website source code:



# 📁 Project Structure

```text
BusBookingAutomation
│
└── src
    └── test
        ├── java
        │   ├── base
        │   │   └── BaseTest.java
        │   │
        │   ├── pages
        │   │   ├── HomePage.java
        │   │   ├── BusPage.java
        │   │   ├── SeatPage.java
        │   │   ├── PassengerPage.java
        │   │   └── PaymentPage.java
        │   │
        │   ├── tests
        │   │   └── BookingTest.java
        │   │
        │   └── utils
        │       └── ConfigReader.java
        │
        └── resources
            └── config.properties
```

---

# 📂 Create Project Folders

## 🪟 Windows

```bat
mkdir src\main\java\base
mkdir src\main\java\pages
mkdir src\test\java\tests
mkdir src\main\java\utils
mkdir src\main\resources
```

## 🍎 macOS / 🐧 Linux

```bash
mkdir -p src/main/java/base
mkdir -p src/main/java/pages
mkdir -p src/test/java/tests
mkdir -p src/main/java/utils
mkdir -p src/main/resources
```

---

# 📄 Create Project Files

## 🪟 Windows

```bat
type nul > src\main\java\base\BaseTest.java

type nul > src\main\java\pages\HomePage.java
type nul > src\main\java\pages\BusPage.java
type nul > src\main\java\pages\SeatPage.java
type nul > src\main\java\pages\PassengerPage.java
type nul > src\main\java\pages\PaymentPage.java

type nul > src\test\java\tests\BookingTest.java

type nul > src\main\java\utils\ConfigReader.java

type nul > src\main\resources\config.properties
```

## 🍎 macOS / 🐧 Linux

```bash
touch src/main/java/base/BaseTest.java

touch src/main/java/pages/HomePage.java
touch src/main/java/pages/BusPage.java
touch src/main/java/pages/SeatPage.java
touch src/main/java/pages/PassengerPage.java
touch src/main/java/pages/PaymentPage.java

touch src/test/java/tests/BookingTest.java

touch src/main/java/utils/ConfigReader.java

touch src/main/resources/config.properties
```



## Config.Properties
```python
url=C:\\Users\\LENOVO\\Downloads\\bus-CU\\bus-CU\\index.html
fromLocation=1
fromDate=2026-08-20





```

# ConfigReader.java

```python
package utils;

import java.io.FileInputStream;
import java.util.Properties;

public class ConfigReader {

    static Properties p=new Properties();

    static  {
        try{
            p.load(new FileInputStream("src\\main\\resources\\config.properties"));
        }
        catch (Exception e){
            e.printStackTrace();

        }
    }
    public static  String get(String key){
        return p.getProperty(key);
    }

    }


```

## base/BaseTest.java

```pyton
package base;
import utils.ConfigReader;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class BaseTest {
    protected WebDriver driver;

    public void Setup() throws Exception{
        driver =new ChromeDriver();
        driver.manage().window().maximize();
        driver.get(ConfigReader.get("url"));
        Thread.sleep(2000);

    }
    public void close() {
        driver.quit();
    }
}


```

## Pages/HomePage.java

```python
package pages;
import org.openqa.selenium.*;
import base.BaseTest;

import org.openqa.selenium.support.ui.Select;
import utils.ConfigReader;

public class HomePage {
    WebDriver driver;

    public  void HomePage(WebDriver driver){
        this.driver=driver;
    }

    public void setLocation(){
        Select from=new Select(driver.findElement(By.name("from")));

        from.selectByIndex(Integer.parseInt(
                ConfigReader.get("fromLocation")
        ));


    }
    public void SelectDate(){

        WebElement date= driver.findElement(By.id("date"));

        JavascriptExecutor js=(JavascriptExecutor) driver;

        js.executeScript("arguments[0].removeAttribute('readnly'));",
        date
        );

        js.executeScript("arguments[0].value='"+
                ConfigReader.get("fromDate")+ "';"+
                "arguments[0].dispatchEvent(new Event('change'));",date
        );
    }

    public void ContniueNext(){
        driver.findElement(By.className("next_button")).click();
    }
}
```
