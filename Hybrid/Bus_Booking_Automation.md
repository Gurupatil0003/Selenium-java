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
mkdir src\test\java\base
mkdir src\test\java\pages
mkdir src\test\java\tests
mkdir src\test\java\utils
mkdir src\test\resources
```

## 🍎 macOS / 🐧 Linux

```bash
mkdir -p src/test/java/base
mkdir -p src/test/java/pages
mkdir -p src/test/java/tests
mkdir -p src/test/java/utils
mkdir -p src/test/resources
```

---

# 📄 Create Project Files

## 🪟 Windows

```bat
type nul > src\test\java\base\BaseTest.java

type nul > src\test\java\pages\HomePage.java
type nul > src\test\java\pages\BusPage.java
type nul > src\test\java\pages\SeatPage.java
type nul > src\test\java\pages\PassengerPage.java
type nul > src\test\java\pages\PaymentPage.java

type nul > src\test\java\tests\BookingTest.java

type nul > src\test\java\utils\ConfigReader.java

type nul > src\test\resources\config.properties
```

## 🍎 macOS / 🐧 Linux

```bash
touch src/test/java/base/BaseTest.java

touch src/test/java/pages/HomePage.java
touch src/test/java/pages/BusPage.java
touch src/test/java/pages/SeatPage.java
touch src/test/java/pages/PassengerPage.java
touch src/test/java/pages/PaymentPage.java

touch src/test/java/tests/BookingTest.java

touch src/test/java/utils/ConfigReader.java

touch src/test/resources/config.properties
```
