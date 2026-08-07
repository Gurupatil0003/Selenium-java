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
