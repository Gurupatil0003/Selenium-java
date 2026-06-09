<img width="1200" height="624" alt="image" src="https://github.com/user-attachments/assets/dc5ee46f-b816-4628-a88a-1415462a356c" />


# Functional Testing Types (Java Examples)

Functional Testing checks whether the software features work as expected.

---

## 1. Unit Testing

### What is it?
Testing a single method or function.

### Java Example

```java
public int add(int a, int b) {
    return a + b;
}
```

Test:

```java
add(2, 3);
```

Expected Output:

```java
5
```

### Purpose
Verify that an individual method works correctly.

---

## 2. Integration Testing

### What is it?
Testing how multiple classes/modules work together.

### Java Example

```java
UserService → DatabaseService
```

Scenario:

- User logs in.
- UserService checks credentials.
- DatabaseService fetches data.

### Purpose
Verify communication between modules.

---

## 3. System Testing

### What is it?
Testing the complete application.

### Java Example

Banking Application:

1. Register User
2. Login
3. Transfer Money
4. View Transaction History

### Purpose
Verify the entire system works correctly.

---

## 4. Smoke Testing

### What is it?
Checking whether the main features work after a new build.

### Java Example

Verify:

- Application starts
- Login page opens
- Database connection works

### Purpose
Ensure the build is stable.

---

## 5. Sanity Testing

### What is it?
Testing a specific functionality after a bug fix.

### Java Example

Bug Fixed:

```java
Forgot Password Feature
```

Test only:

```java
Forgot Password Module
```

### Purpose
Confirm the bug fix works correctly.

---

## 6. Regression Testing

### What is it?
Testing existing features after adding new code.

### Java Example

New Feature Added:

```java
UPI Payment
```

Retest:

- Login
- Account Balance
- Money Transfer

### Purpose
Ensure old features still work.

---

## 7. User Acceptance Testing (UAT)

### What is it?
Testing by clients or end users.

### Java Example

Client verifies:

- Account creation
- Fund transfer
- Statement generation

### Purpose
Ensure business requirements are met.

---

## 8. API Testing

### What is it?
Testing backend APIs without the UI.

### Java Example

API:

```http
POST /login
```

Request:

```json
{
  "username":"admin",
  "password":"123"
}
```

Response:

```json
{
  "status":"success"
}
```

### Purpose
Verify API functionality.

---

## 9. End-to-End (E2E) Testing

### What is it?
Testing a complete user workflow.

### Java Example

Online Shopping Application:

1. Register
2. Login
3. Search Product
4. Add to Cart
5. Make Payment
6. Place Order

### Purpose
Verify the complete user journey.

---

# Quick Interview Answer

### Functional Testing Types

1. Unit Testing
2. Integration Testing
3. System Testing
4. Smoke Testing
5. Sanity Testing
6. Regression Testing
7. User Acceptance Testing (UAT)
8. API Testing
9. End-to-End Testing (E2E)

**Remember:**

- Unit → Single Method
- Integration → Multiple Modules
- System → Entire Application
- Smoke → Basic Build Check
- Sanity → Check Bug Fix
- Regression → Ensure Old Features Work
- UAT → Client Validation
- API → Backend Testing
- E2E → Complete User Flow
