```python

232
│
├── pom.xml
│
├── src
│   │
│   ├── main
│   │   └── java
│   │       │
│   │       ├── base
│   │       │    └── BaseTest.java
│   │       │
│   │       ├── pages
│   │       │    └── WikipediaPage.java
│   │       │
│   │       └── utils
│   │            └── ConfigReader.java
│   │
│   └── test
│       │
│       ├── java
│       │    └── tests
│       │         └── WikiTest.java
│       │
│       └── resources
│            └── config.properties


```




```python


mkdir src\main\java\base
mkdir src\main\java\pages
mkdir src\main\java\utils
```
Create test folder:
```python

mkdir src\test\java\tests
mkdir src\test\resources
```
Create files:
```python
New-Item src\main\java\base\BaseTest.java
New-Item src\main\java\pages\WikipediaPage.java
New-Item src\main\java\utils\ConfigReader.java

New-Item src\test\java\tests\WikiTest.java

New-Item src\test\resources\config.properties
```


## BaseTest.java
```python
package base;
import utils.ConfigReader;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class BaseTest {
    public static WebDriver driver;

    public void start() throws Exception{
        driver=new ChromeDriver();
        driver.manage().window().maximize();

        driver.get(ConfigReader.get("url"));
        Thread.sleep(2000);

    }
    public void end(){
        driver.quit();
    }
}

```


## WikipediaPage.java

```python

package pages;
import base.BaseTest;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;

public class WikipediaPage {
    WebDriver driver;

    public WikipediaPage(WebDriver driver) {
        this.driver=driver;

    }


    public void Search(String text ) throws  Exception{
        driver.findElement(By.name("search")).sendKeys(text);
        Thread.sleep(2000);

        driver.findElement(By.xpath("//button[@type='submit']"))
                .click();
        Thread.sleep(2000);
    }
}

```


## ConfigReader.java
```python



package utils;
import java.io.FileInputStream;
import java.util.Properties;

public class ConfigReader {
    static Properties p=new Properties();


    static {
        try{
            p.load(new FileInputStream("src\\test\\resources\\config.properties"));
        }
        catch (Exception e){
            e.printStackTrace();

        }
    }
    public static String get(String key){
        return p.getProperty(key);
    }
}

```


## WikiTest.java
```python

package tests;

import base.BaseTest;
import pages.WikipediaPage;
import utils.ConfigReader;

import org.testng.annotations.Test;

public class WikiTest extends  BaseTest{






    }
}




```

COnfig.proparties


```python
url=https://www.wikipedia.org/
Search=selenium



```
