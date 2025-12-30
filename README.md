# JMeter API Testing – Login and Get User Info

This project demonstrates basic API testing using **Apache JMeter** with a chained request flow: Login → Extract Token → Use Token in subsequent request.


## Live JMeter Report
🔗 [View Live Report](https://mousavianhanieh.github.io/JMeter-LoadTest-Login/report/)



## Tech Stack
- Apache JMeter
- REST API Testing
- JSON Assertions
- HTTP Header Management

---

## Test Scenario

### 1. Login API
- Method: POST
- Endpoint: `/api/login` (https://reqres.in)
- Request Body:
```json
{
  "email": "eve.holt@reqres.in",
  "password": "cityslicka"
}
```
Headers:
Content-Type: application/json

Validation:

- JSON Assertion: $.token exists

- Success scenario: Token extracted

- Failure scenario: Missing/incorrect password → Error response handled

---
### 2. Get User Info

Method: GET

Endpoint: /api/users/2

Headers:
Authorization: Bearer ${auth_token}

Validation:

- JSON Assertion: $.data.id = 2

### Load Test Settings

- Number of Threads (Users): 5–10

- Ramp-up Period: 10 sec

- Loop Count: 1

Users gradually log in and fetch user info to simulate light load.
