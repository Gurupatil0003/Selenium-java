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

```python
# 🐳 Docker Compose Multi Container Deployment Demo

This project demonstrates a **multi-container deployment using Docker Compose**.

Docker Compose allows us to define and manage multiple Docker containers using a single YAML configuration file (`docker-compose.yml`).

In this demo we are running:

- 🌐 Nginx Web Server Container
- 🛠️ BusyBox Helper Container


---

# 📂 Project Structure

```
docker-compose-demo
│
├── docker-compose.yml
│
├── website
│   └── index.html
│
└── README.md
```


---

# Why Docker Compose?

Without Docker Compose, we need to manually run multiple Docker commands:

Example:

```bash
docker run -d -p 8081:80 nginx
docker run busybox
```

For larger applications containing:

- Frontend
- Backend
- Database
- Cache
- Message Queue

Managing containers manually becomes difficult.

Docker Compose solves this problem by storing all container configurations in one YAML file.

With one command:

```bash
docker compose up
```

all containers are created and started automatically.


---

# 📝 docker-compose.yml Explanation

Complete file:

```yaml
version: "3.8"

services:

  web:
    image: nginx:latest
    container_name: nginx-demo
    ports:
      - "8081:80"
    volumes:
      - ./website:/usr/share/nginx/html


  busybox:
    image: busybox
    container_name: helper-container
    command: sh -c "while true; do echo Multi Container Running...; sleep 10; done"
```


---

# YAML Configuration Explanation

## 1. Version

```yaml
version: "3.8"
```

Defines Docker Compose file version.

Docker Compose supports different versions:

```
2.x
3.x
3.8
3.9
```

Version `3.8` provides support for modern Docker features.


---

# 2. Services

```yaml
services:
```

Services represent Docker containers.

Example:

```
services

 |
 |---- web container
 |
 |---- busybox container
```


In this project we have two services:

```
web
 |
 nginx container


busybox
 |
 helper container
```


---

# 🌐 Web Service

```yaml
web:
```

This is the service name.

A service defines how a container should run.


---

# Image

```yaml
image: nginx:latest
```

Defines the Docker image.

Format:

```
image_name:version
```

Example:

```
nginx:latest
```

Docker downloads this image from Docker Hub.


Equivalent command:

```bash
docker pull nginx:latest
```


---

# Container Name

```yaml
container_name: nginx-demo
```

Defines a custom container name.

Without this Docker creates random names.

Example:

```
nginx-demo
```

Now we can easily manage it:

```bash
docker logs nginx-demo
```


---

# Port Mapping

```yaml
ports:
 - "8081:80"
```

Port format:

```
HOST PORT : CONTAINER PORT
```

Meaning:

```
Your Computer              Docker Container

localhost:8081  -------->  nginx port 80
```


Open browser:

```
http://localhost:8081
```

You can access the website.


---

# Volume Mapping

```yaml
volumes:
 - ./website:/usr/share/nginx/html
```

Volume connects a local folder with a container folder.


Format:

```
LOCAL PATH : CONTAINER PATH
```


Example:

```
Computer

website
 |
 └── index.html


        |
        |
        v


Container

/usr/share/nginx/html
 |
 └── index.html
```


Advantages:

- Changes reflect immediately
- No need to rebuild image
- Data can persist


---

# 🛠️ BusyBox Service

```yaml
busybox:
```

Second container in our application.


BusyBox is a lightweight Linux image used for:

- Testing
- Debugging
- Running small commands


---

# BusyBox Image

```yaml
image: busybox
```

Downloads:

```
busybox:latest
```


Equivalent:

```bash
docker pull busybox
```


---

# BusyBox Container Name

```yaml
container_name: helper-container
```

Creates container:

```
helper-container
```


---

# Command Explanation

```yaml
command: sh -c "while true; do echo Multi Container Running...; sleep 10; done"
```


Breaking it down:


## sh

Starts Linux shell.

```
sh
```


## -c

Executes the provided command.

Example:

```bash
sh -c "ls"
```


## While Loop

```bash
while true
```

Runs continuously.


Flow:

```
Start
 |
Print message
 |
Wait 10 seconds
 |
Repeat
```


## Echo

```bash
echo Multi Container Running...
```

Prints:

```
Multi Container Running...
```


## Sleep

```bash
sleep 10
```

Waits 10 seconds before next execution.


Output:

```
Multi Container Running...

(wait 10 seconds)

Multi Container Running...

(wait 10 seconds)

Multi Container Running...
```


---

# 🏗️ Application Architecture


```
                 Docker Compose

                       |
        --------------------------------
        |                              |
        |                              |

   nginx-demo                  helper-container

   nginx image                busybox image

       |
       |
 Port 80

       |
       |

localhost:8081


       |
       |

 website/index.html
```


---

# ▶️ How to Run


## Step 1: Create Website File

Create:

```
website/index.html
```


Example:

```html
<html>

<body>

<h1>
Docker Compose Demo
</h1>

<p>
Nginx Container Running Successfully
</p>

</body>

</html>
```


---

## Step 2: Start Containers


Run:

```bash
docker compose up
```


Docker will:

- Create containers
- Create network
- Start services


---

# Run in Background

Use detached mode:

```bash
docker compose up -d
```


`-d` means:

```
Run containers in background
```


---

# Check Running Containers


Command:

```bash
docker ps
```


Example output:

```
CONTAINER NAME

nginx-demo

helper-container
```


---

# View Logs


Nginx logs:

```bash
docker logs nginx-demo
```


BusyBox logs:

```bash
docker logs helper-container
```


---

# Stop Application


Command:

```bash
docker compose down
```


This removes:

- Containers
- Docker Compose network


---

# Useful Docker Compose Commands


## Start containers

```bash
docker compose up
```


## Start in background

```bash
docker compose up -d
```


## Stop containers

```bash
docker compose down
```


## Check services

```bash
docker compose ps
```


## View logs

```bash
docker compose logs
```


---

# Real World Usage

Docker Compose is commonly used for applications containing:


```
Frontend
   |
React Container


Backend
   |
Java / Python Container


Database
   |
MySQL Container


Cache
   |
Redis Container
```


All can be managed using:

```bash
docker compose up
```


---

# Conclusion

Docker Compose simplifies multi-container deployment by allowing developers to define:

✅ Containers  
✅ Images  
✅ Ports  
✅ Volumes  
✅ Commands  
✅ Networks  

inside a single YAML file.

This makes application deployment faster, repeatable, and easier to maintain.




```
