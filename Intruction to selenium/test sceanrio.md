# Test Scenario Design

## Flow of Test Scenario Design

```text
Requirement Gathering
        ↓
Understand Business Requirements
        ↓
Identify Functionalities
        ↓
Break Down Modules
        ↓
Identify Positive Scenarios
        ↓
Identify Negative Scenarios
        ↓
Identify Boundary Conditions
        ↓
Identify Exception/Error Scenarios
        ↓
Prioritize Scenarios
        ↓
Review with Team/BA
        ↓
Create Test Cases
        ↓
Execute Test Cases
```

---

# Login Module

## Requirements
- User should be able to log in using valid credentials.
- Invalid credentials should display an error message.
- Account should be locked after multiple failed attempts.

## Positive Test Scenarios

| TS ID | Scenario |
|---------|----------|
| TS_001 | Verify login with valid username and password |
| TS_002 | Verify successful navigation to dashboard |
| TS_003 | Verify login button functionality |

## Negative Test Scenarios

| TS ID | Scenario |
|---------|----------|
| TS_004 | Verify login with invalid username |
| TS_005 | Verify login with invalid password |
| TS_006 | Verify login with empty username and password |
| TS_007 | Verify login with special characters |
| TS_008 | Verify SQL injection prevention |

## Boundary Test Scenarios

| TS ID | Scenario |
|---------|----------|
| TS_009 | Verify minimum username length |
| TS_010 | Verify maximum username length |
| TS_011 | Verify password length limits |

## Exception Scenarios

| TS ID | Scenario |
|---------|----------|
| TS_012 | Verify account lock after 5 failed attempts |
| TS_013 | Verify system behavior when server is unavailable |
| TS_014 | Verify session timeout functionality |

## Non-Functional Test Scenarios

| TS ID | Scenario |
|---------|----------|
| TS_015 | Verify login response time |
| TS_016 | Verify concurrent user login handling |
| TS_017 | Verify browser compatibility |
| TS_018 | Verify password encryption and security |

---

# Overall Test Scenario Design Process

```text
Requirement Document
        ↓
Analyze Requirements
        ↓
Identify Modules
        ↓
Positive Scenarios
Negative Scenarios
Boundary Scenarios
Exception Scenarios
Security Scenarios
Performance Scenarios
Compatibility Scenarios
Accessibility Scenarios
        ↓
Review Scenarios
        ↓
Create Test Cases
        ↓
Execute Test Cases
```

---

# Example Modules

## Registration Module
- Valid registration
- Invalid email
- Mandatory field validation
- Duplicate account check
- Password strength validation
- Email verification

## Search Module
- Valid search
- Invalid search
- Empty search
- Partial keyword search
- Search response time

## Cart Module
- Add item
- Remove item
- Update quantity
- Empty cart validation
- Multiple item handling

## Payment Module
- Successful payment
- Invalid card details
- Payment timeout
- Payment failure
- Security validation

## Order Module
- Place order
- Cancel order
- Refund process
- View order history
- Concurrent order handling
