# Log4j2 Logging Levels

## Why Do We Need Log4j2?

Log4j2 is a Java logging framework used to record application events. Instead of using `System.out.println()`, Log4j2 provides structured logging that helps developers and testers to:

- Debug application issues quickly.
- Track the execution flow of the application.
- Identify where failures occur.
- Store logs in files for future analysis.
- Control which log messages are displayed using log levels.
- Improve application monitoring and maintenance.

---

# Log4j2 Logging Levels

Log4j2 provides **7 logging levels**, arranged from the lowest severity to the highest.

| Level | Purpose | Example |
| :---: | ------- | ------- |
| **TRACE** | Used for very detailed execution information. Helps trace every step of the application. | `log.trace("Entering Password");` |
| **DEBUG** | Used during development to debug the application and verify program flow. | `log.debug("Entering Username");` |
| **INFO** | Used for general application events that indicate normal execution. | `log.info("Launching Chrome Browser");` |
| **WARN** | Indicates a potential issue that does not stop the application. | `log.warn("Hardcoded credentials are used.");` |
| **ERROR** | Indicates an error occurred, but the application may continue running. | `log.error("Login Failed");` |
| **FATAL** | Indicates a critical error that may cause the application to stop. | `log.fatal("Application crashed.");` |
| **OFF** | Disables all logging. This is a configuration level, not a logging method. | `Configurator.setRootLevel(Level.OFF);` |

---

## Logging Level Priority

```text
TRACE
   ↓
DEBUG
   ↓
INFO
   ↓
WARN
   ↓
ERROR
   ↓
FATAL
   ↓
OFF (Disables all logging)
````

---

## Summary

| Logging Level | Description                                                 |
| ------------- | ----------------------------------------------------------- |
| **TRACE**     | Records very detailed execution information.                |
| **DEBUG**     | Used for debugging and troubleshooting during development.  |
| **INFO**      | Records normal application events.                          |
| **WARN**      | Indicates a warning that does not stop the application.     |
| **ERROR**     | Records errors that affect application functionality.       |
| **FATAL**     | Records critical errors that may terminate the application. |
| **OFF**       | Disables all logging output.                                |

---

## Why Use Log4j2 Instead of `System.out.println()`?

| `System.out.println()`                     | Log4j2                                                              |
| ------------------------------------------ | ------------------------------------------------------------------- |
| Prints plain text to the console           | Supports multiple logging levels                                    |
| No severity classification                 | Categorizes logs using TRACE, DEBUG, INFO, WARN, ERROR, and FATAL   |
| Cannot enable or disable specific messages | Log levels can be configured dynamically                            |
| Difficult to debug large applications      | Makes debugging and monitoring easier                               |
| Console output only                        | Can write logs to console, files, databases, and other destinations |

---

## Conclusion

Log4j2 provides a structured and configurable way to log application events. By using different logging levels, developers and testers can easily monitor application behavior, debug issues, identify failures, and maintain applications more efficiently.

```
```
```python
<?xml version="1.0" encoding="UTF-8"?>
<Configuration status="WARN">

    <Appenders>

        <Console name="Console" target="SYSTEM_OUT">
            <PatternLayout
                    pattern="%d{HH:mm:ss} %-5level %msg%n"/>
        </Console>

    </Appenders>

    <Loggers>

        <Root level="trace">
            <AppenderRef ref="Console"/>
        </Root>

    </Loggers>

</Configuration>
```

```python
        <dependency>
            <groupId>org.apache.logging.log4j</groupId>
            <artifactId>log4j-api</artifactId>
            <version>2.23.1</version>
        </dependency>

        <dependency>
            <groupId>org.apache.logging.log4j</groupId>
            <artifactId>log4j-core</artifactId>
            <version>2.23.1</version>
        </dependency>
```
