# Booking API - DELETE Test Cases

## Test Environment

- **API:** Restful Booker
- **Base URL:** `https://restful-booker.herokuapp.com`
- **Tool:** Postman
- **OS:** Windows 11
- **Environment:** Restful Booker Environment

## Test Cases Summary

| ID | Title | Priority | Type |
|---|---|---|---|
| C335 | Delete existing booking with token | High | Functional |
| C336 | Delete without authorization | High | Security |
| C337 | Verify Deleted Booking | High | Functional |

## C335 — Delete existing booking with token

**Priority:** High  
**Type:** Functional

### Preconditions

1. Postman is opened.
2. Postman environment is selected.
3. baseUrl is set to https://restful-booker.herokuapp.com.
4. A valid token is generated.
5. A valid booking exists.
6. bookingId variable contains a valid booking ID.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a DELETE request to {{baseUrl}}/booking/{{bookingId}}. | Request URL is prepared with valid booking ID. |
| 2 | Set header Cookie: token={{token}}. | Valid token is added. |
| 3 | Send the request. | API returns 201 Created. |

## C336 — Delete without authorization

**Priority:** High  
**Type:** Security

### Preconditions

1. Postman is opened.
2. Postman environment is selected.
3. baseUrl is set to https://restful-booker.herokuapp.com.
4. A valid booking exists.
5. bookingId variable contains a valid booking ID.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a DELETE request to {{baseUrl}}/booking/{{bookingId}}. | Request URL is prepared with valid booking ID. |
| 2 | Do not add authorization token. | Header remains without authorization token. |
| 3 | Send the request. | API returns 403 Forbidden. |

## C337 — Verify Deleted Booking

**Priority:** High  
**Type:** Functional

### Preconditions

1. Postman is opened.
2. Postman environment is selected.
3. baseUrl is set to https://restful-booker.herokuapp.com.
4. A booking was deleted successfully.
5. bookingId variable contains the deleted booking ID.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a GET request to {{baseUrl}}/booking/{{bookingId}}. | Request URL is prepared with deleted booking ID. |
| 2 | Set header Accept: application/json. | Header is added. |
| 3 | Send the request. | API returns 404 Not Found. Deleted booking is not available. |
