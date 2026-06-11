<img width="864" height="1821" alt="image" src="https://github.com/user-attachments/assets/505639dc-3050-4ea2-a619-002b0c54a428" />


# Software Testing Levels

Software Testing Levels define **where and when testing is performed** during software development.

There are **4 main levels of testing**:

## 1. Unit Testing

### What is it?
Testing a single method or function.

### Example
```java
add(5, 3);
```

Expected Output:

```java
8
```

### Goal
Ensure individual code units work correctly.

---

## 2. Integration Testing

### What is it?
Testing whether multiple modules work together correctly.

### Example
```text
Login Module → Database Module
```

### Goal
Verify communication between modules.

---

## 3. System Testing

### What is it?
Testing the complete application as a whole.

### Example
```text
Login → Add Product → Payment → Logout
```

### Goal
Ensure the entire system works as expected.

---

## 4. Acceptance Testing (UAT)

### What is it?
Testing performed by the client or end users before release.

### Example
```text
Client verifies all business requirements are met.
```

### Goal
Ensure the software is ready for production use.

---

# Testing Levels Flow

```text
Unit Testing
      ↓
Integration Testing
      ↓
System Testing
      ↓
Acceptance Testing (UAT)
      ↓
Production
```

# Quick Summary

| Level | Purpose |
|---------|----------|
| Unit Testing | Test a single method/function |
| Integration Testing | Test module interaction |
| System Testing | Test complete application |
| Acceptance Testing | Validate business requirements |

### Easy Memory Trick

**UISA**

- U → Unit
- I → Integration
- S → System
- A → Acceptance


Blog
https://medium.com/p/2fa2ae225886/edit
