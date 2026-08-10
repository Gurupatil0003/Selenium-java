```python
package pages;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;

public class HomePage {

    WebDriver driver;

    public HomePage(WebDriver driver) {
        this.driver = driver;
    }

    public void openWebsite() {

        driver.get(
                "https://mouneshgouda.github.io/HotelBooking/"
        );
    }


    public void searchRoom(String checkIn, String checkOut, String guests) {

        driver.findElement(By.id("checkIn"))
                .sendKeys(checkIn);

        driver.findElement(By.id("checkOut"))
                .sendKeys(checkOut);

        driver.findElement(By.id("guests"))
                .sendKeys(guests);

        driver.findElement(By.id("searchRooms"))
                .click();
    }
}

```

```python



```
