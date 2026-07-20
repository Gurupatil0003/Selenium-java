```python
import java.sql.*;
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;

public class hello {

    public static void main(String[] args) throws Exception {

        ChromeDriver driver = new ChromeDriver();
        driver.manage().window().maximize();
        driver.get("file:///C:/Users/LENOVO/IdeaProjects/simpe/reports/report.html");

        Connection con = DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/seleniumcru",
                "root",
                "mgpatils");

        // CREATE
        driver.findElement(By.id("name")).sendKeys("Guru");
        driver.findElement(By.id("email")).sendKeys("guru@gmail.com");

        con.prepareStatement(
                        "insert into users(name,email) values('Guru','guru@gmail.com')")
                .executeUpdate();

        System.out.println("User Added");
        Thread.sleep(2000);

        // READ
        showUsers(con);

        // UPDATE
        driver.findElement(By.id("name")).clear();
        driver.findElement(By.id("email")).clear();

        driver.findElement(By.id("name")).sendKeys("Guru Updated");
        driver.findElement(By.id("email")).sendKeys("guru123@gmail.com");

        con.prepareStatement(
                        "update users set name='Guru Updated',email='guru123@gmail.com' where id=1")
                .executeUpdate();

        System.out.println("\nUser Updated");
        Thread.sleep(2000);

        // DELETE
        con.prepareStatement("delete from users where id=2").executeUpdate();

//        System.out.println("User Deleted");
        Thread.sleep(2000);

        // READ AGAIN
        showUsers(con);

        con.close();
        driver.quit();
    }

    static void showUsers(Connection con) throws Exception {

        ResultSet rs = con.createStatement().executeQuery("select * from users");

        System.out.println("\nUsers");

        while (rs.next())
            System.out.println(rs.getInt(1) + "  " +
                    rs.getString(2) + "  " +
                    rs.getString(3));
    }
}


```

```python
<!DOCTYPE html>
<html>
<head>
    <title>Simple CRUD</title>
</head>
<body>

<h2>User Form</h2>

Name:
<input type="text" id="name"><br><br>

Email:
<input type="text" id="email"><br><br>

<button id="add">Add</button>
<button id="update">Update</button>
<button id="delete">Delete</button>
<button id="read">Read</button>

</body>
</html>

```

```python
CREATE DATABASE seleniumcru;

USE seleniumcru;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100)
);

INSERT INTO users(name,email)
VALUES
('John','john@gmail.com'),
('Alice','alice@gmail.com');

select *from users;


```
