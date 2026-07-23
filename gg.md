# AWS IAM Hands-on Lab (User + Group + Policy)

## Objective

Learn to create an IAM User, Group, and Custom Policy and grant S3
access.

## Steps

### 1. Create an S3 Bucket

Bucket name: `guru-demo-bucket`

### 2. Create an IAM User

IAM → Users → Create user

Username: `guru`

### 3. Create an IAM Group

IAM → User groups → Create group

Group: `Developers`

### 4. Add User to Group

Add user `guru` to `Developers`.

### 5. Create a Custom Policy

IAM → Policies → Create policy → JSON

``` json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:ListAllMyBuckets",
        "s3:GetBucketLocation"
      ],
      "Resource": "*"
    }
  ]
}
```

Policy name: `MyS3Policy`

### 6. Attach Policy to Group

IAM → User groups → Developers → Permissions → Add permissions

Select `MyS3Policy`.

### 7. Login as IAM User

Sign out from root and log in as `guru`.

### 8. Verify

Open S3. The user can list buckets but cannot delete them.

## Flow

``` text
Custom Policy
      |
      v
Developers Group
      |
      v
IAM User (guru)
      |
      v
Amazon S3
```


```python

# Build image
docker build -t flask-demo .

# Create container
docker run -d -p 5000:5000 --name flask-container flask-demo

# Check
docker ps

# Stop
docker stop flask-container

# Remove container
docker rm flask-container

# Remove image
docker rmi flask-demo

```

```python
# app/main.py
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
 return 'Hello, World!'
if __name__ == '__main__':
 app.run(host='0.0.0.0', port=5000)


```

```python
Flask==2.2.5
Werkzeug==2.2.3

```

```python
#FROM eclipse-temurin:21-jdk
#
#WORKDIR app/
#
#COPY /src/main/java/gg.java .
#
#RUN javac gg.java
#
#CMD ["java","gg"]
#
#
#

# Python base image
FROM python:3.9-slim

# Working directory inside container
WORKDIR /app

# Copy requirements
COPY src/main/java/requirements.txt .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY src/main/java/ .

# Run application
CMD ["python", "app.py"]



```

```python

# app/main.py
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
 return 'Hello, World!'
if __name__ == '__main__':
 app.run(host='0.0.0.0', port=5000)

```


```python

# Build image
docker build -t flask-demo .

# Create container
docker run -d -p 5000:5000 --name flask-container flask-demo

# Check
docker ps

# Stop
docker stop flask-container

# Remove container
docker rm flask-container

# Remove image
docker rmi flask-demo

```


```python
docker network create mynetwork

docker run -dit --name container1 --network mynetwork ubuntu

docker run -dit --name container2 --network mynetwork ubuntu

docker exec -it container1 bash

ping container2

exit

docker network inspect mynetwork

docker network ls

docker rm -f container1 container2

docker network rm mynetwork



apt update
apt install -y iputils-ping
```





### 1. BaseTest.java (short)
```python
package base;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import utils.ConfigReader;

public class BaseTest {

    public static WebDriver driver;

    public void start() throws Exception {

        driver = new ChromeDriver();

        driver.manage().window().maximize();

        Thread.sleep(2000);

        driver.get(ConfigReader.get("url"));

        Thread.sleep(3000);
    }


    public void end(){

        driver.quit();

    }
}
```
## 2. ConfigReader.java (short)
```python
package utils;

import java.io.FileInputStream;
import java.util.Properties;

public class ConfigReader {


static Properties p = new Properties();


static {

try {

p.load(new FileInputStream(
"src/test/resources/config.properties"));

}
catch(Exception e){

e.printStackTrace();

}

}


public static String get(String key){

return p.getProperty(key);

}

}
```
## 3. WikipediaPage.java (short)
```python
package pages;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;


public class WikipediaPage {


WebDriver driver;


public WikipediaPage(WebDriver driver){

this.driver = driver;

}


public void search(String text) throws Exception {


driver.findElement(
By.id("searchInput"))
.sendKeys(text);


Thread.sleep(2000);


driver.findElement(
By.xpath("//button[@type='submit']"))
.click();


Thread.sleep(5000);


}

}
```
### 4. WikiTest.java (short)
```python
package tests;


import org.testng.annotations.Test;

import base.BaseTest;
import pages.WikipediaPage;
import utils.ConfigReader;


public class WikiTest extends BaseTest {


@Test
public void searchWiki() throws Exception {


start();


WikipediaPage page =
new WikipediaPage(driver);


page.search(
ConfigReader.get("search")
);


System.out.println(
driver.getTitle()
);


end();

}

}
```
5. config.properties
```python
url=https://www.wikipedia.org
search=Selenium WebDriver

```
