# 🚌 Bus Booking Automation Framework

This project demonstrates a **Hybrid Selenium Automation Framework** using **Java, Maven, TestNG, and Page Object Model (POM)** to automate a bus booking application.

---

## 📥 Download Source Code

Click below to download the original bus booking website source code:


[Download ZIP](https://github.com/james-muriithi/bus/archive/refs/heads/master.zip)

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

## Config.Proparies

```python

url=file:///C:/Users/LENOVO/Downloads/bus-CU/bus-CU/index.html

fromLocation=1
travelDate=2026-08-15

name=Guru Patil
idNumber=12345678
phone=0712345678
email=guru@gmail.com

```

## ConfigReader

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

```python
package base;


import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import utils.ConfigReader;


public class BaseTest {


    protected WebDriver driver;



    public void setup(){


        driver = new ChromeDriver();


        driver.manage()
                .window()
                .maximize();



        driver.get(
                ConfigReader.get("url")
        );


    }



    public void close(){

        driver.quit();

    }


}


```


## Pages/Homepage.java

```python

package pages;


import org.openqa.selenium.*;
import org.openqa.selenium.support.ui.Select;
import utils.ConfigReader;



public class HomePage {


    WebDriver driver;


    public HomePage(WebDriver driver){

        this.driver=driver;

    }



    public void selectLocation(){


        Select from =
                new Select(
                        driver.findElement(By.name("from"))
                );



        from.selectByIndex(
                Integer.parseInt(
                        ConfigReader.get("fromLocation")
                )
        );


    }



    public void selectDate(){


        WebElement date =
                driver.findElement(By.id("date"));


        JavascriptExecutor js =
                (JavascriptExecutor)driver;



        js.executeScript(
                "arguments[0].removeAttribute('readonly');",
                date
        );



        js.executeScript(
                "arguments[0].value='"+
                        ConfigReader.get("travelDate")+
                        "';"+
                        "arguments[0].dispatchEvent(new Event('change'));",
                date
        );



    }



    public void clickNext(){


        driver.findElement(
                        By.className("next_button")
                )
                .click();


    }


}

```

## pages/BusSeat.java

```python
=package pages;


import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;



public class BusPage {


    WebDriver driver;


    public BusPage(WebDriver driver){

        this.driver=driver;

    }



    public void selectBus(){


        driver.findElement(
                        By.cssSelector(".book_btn")
                )
                .click();


    }


}


```


## Pages/Seatpage.java


```python

package pages;


import org.openqa.selenium.*;
import java.util.List;



public class SeatPage {


    WebDriver driver;


    public SeatPage(WebDriver driver){

        this.driver=driver;

    }



    public void selectSeat(){


        JavascriptExecutor js =
                (JavascriptExecutor)driver;



        List<WebElement> seats =
                driver.findElements(
                        By.id("1_1")
                );



        if(seats.size()>0){


            js.executeScript(
                    "arguments[0].scrollIntoView(true);",
                    seats.get(0)
            );



            js.executeScript(
                    "arguments[0].click();",
                    seats.get(0)
            );



        }


    }



    public void continueSeat(){


        driver.findElement(
                        By.className("btn-booked")
                )
                .click();


    }


}

```

## pages/Passanger.java

```python

package pages;


import org.openqa.selenium.*;
import utils.ConfigReader;


import java.util.List;


public class PassengerPage {


    WebDriver driver;


    public PassengerPage(WebDriver driver){

        this.driver=driver;

    }



    public void enterDetails(){


        driver.findElement(By.id("name"))
                .sendKeys(
                        ConfigReader.get("name")
                );



        driver.findElement(By.id("id"))
                .sendKeys(
                        ConfigReader.get("idNumber")
                );



        driver.findElement(By.id("phone"))
                .sendKeys(
                        ConfigReader.get("phone")
                );



        driver.findElement(By.id("email"))
                .sendKeys(
                        ConfigReader.get("email")
                );


    }




    public void continuePassenger(){


        List<WebElement> buttons =
                driver.findElements(
                        By.xpath("//button[text()='Continue']")
                );



        buttons
                .get(buttons.size()-1)
                .click();



    }


}


```


## Pages/Payment

```python
package pages;


import org.openqa.selenium.*;
import java.util.List;


public class PaymentPage {


    WebDriver driver;


    public PaymentPage(WebDriver driver){

        this.driver=driver;

    }



    public void finishBooking(){


        List<WebElement> finishButtons =
                driver.findElements(
                        By.className("next_button")
                );



        finishButtons
                .get(finishButtons.size()-1)
                .click();


    }


}

```


tests/BookingTest.java

```python

package tests;


import base.BaseTest;
import pages.*;


public class BookingTest extends BaseTest {


    public static void main(String[] args) throws Exception {


        BookingTest test = new BookingTest();


        // Open Browser
        test.setup();


        System.out.println("Website Opened");



        // Home Page
        HomePage home =
                new HomePage(test.driver);


        home.selectLocation();

        Thread.sleep(2000);


        home.selectDate();

        Thread.sleep(2000);


        home.clickNext();


        Thread.sleep(5000);



        // Bus Page
        BusPage bus =
                new BusPage(test.driver);


        bus.selectBus();


        Thread.sleep(5000);



        // Seat Page
        SeatPage seat =
                new SeatPage(test.driver);


        seat.selectSeat();


        Thread.sleep(3000);


        seat.continueSeat();


        Thread.sleep(4000);



        // Passenger Page
        PassengerPage passenger =
                new PassengerPage(test.driver);


        passenger.enterDetails();


        Thread.sleep(3000);


        passenger.continuePassenger();


        Thread.sleep(4000);



        // Payment Page
        PaymentPage payment =
                new PaymentPage(test.driver);


        payment.finishBooking();


        Thread.sleep(6000);



        System.out.println(
                "BOOKING COMPLETED SUCCESSFULLY"
        );



        // Close Browser
        test.close();


    }


}

```
