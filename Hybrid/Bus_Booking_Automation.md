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
