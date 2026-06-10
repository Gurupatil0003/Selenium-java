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
