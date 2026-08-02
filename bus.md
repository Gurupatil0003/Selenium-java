## Config.Properties
```python

url=file:///C:/Users/LENOVO/Downloads/bus-CU/bus-CU/index.html

fromLocation=1
travelDate=2026-08-15

name=Guru Patil
idNumber=12345678
phone=0712345678
email=guru@gmail.com
```


## ConfigRedaer


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

## pages/Homepage
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

## BasePage
```python
package pages;


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

## Seatpage


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
                        By.cssSelector(".seatCharts-seat.available")
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

## Passangerpage

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

## payment

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

## java/test/BookingTest
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

