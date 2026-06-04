# Booking API - POST Test Cases

## Test Environment

- **API:** Restful Booker
- **Base URL:** `https://restful-booker.herokuapp.com`
- **Tool:** Postman
- **OS:** Windows 11
- **Environment:** Restful Booker Environment

## Test Cases Summary

| ID | Title | Priority | Type |
|---|---|---|---|
| C327 | Create booking with valid data | High | Functional |
| C328 | Create booking without required totalprice | High | Functional |
| C329 | Create booking with checkout earlier than checkin | High | Functional |
| C338 | Create Booking accepts invalid data types | High | Functional |

## C327 — Create booking with valid data

**Priority:** High  
**Type:** Functional  

### Preconditions

1. Postman is opened.
2. Postman environment is selected.
3. baseUrl is set to https://restful-booker.herokuapp.com.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a `POST` request to `{{baseUrl}}/booking`. | Request URL is prepared. |
| 2 | Set headers: `Content-Type: application/json`, `Accept: application/json`. | Headers are added. |
| 3 | Add valid booking data in request body. | Request body contains valid booking data. |
| 4 | Send the request. | API returns `200 OK and response contains bookingid` and booking object. |

## C328 — Create booking without required totalprice

**Priority:** High  
**Type:** Functional  

### Preconditions

1. Postman is opened.
2. Postman environment is selected.
3. baseUrl is set to https://restful-booker.herokuapp.com.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a `POST` request to `{{baseUrl}}/booking`. | Request URL is prepared. |
| 2 | Set headers: `Content-Type: application/json`, `Accept: application/json`. | Headers are added. |
| 3 | Add booking data in request body without the required `totalprice` field. | Request body does not contain `totalprice`. |
| 4 | Send the request. | API should return `400 Bad Request` with validation error and booking should not be created. |

**Known Issue:** API returns `500 Internal Server Error` instead of `400 Bad Request` when `totalprice` is missing.

## C329 — Create booking with checkout earlier than checkin

**Priority:** High  
**Type:** Functional  

### Preconditions

1. Postman is opened.
2. Postman environment is selected.
3. baseUrl is set to https://restful-booker.herokuapp.com.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a `POST` request to `{{baseUrl}}/booking`. | Request URL is prepared. |
| 2 | Set headers: `Content-Type: application/json`, `Accept: application/json`. | Headers are added. |
| 3 | Add valid booking data in request body, where `checkout` date is earlier than `checkin` date. | Request body contains invalid date range. |
| 4 | Send the request. | API should return `400 Bad Request` with validation error and booking should not be created. |

**Known Issue:** API returns `200 OK` and creates a booking when `checkout` date is earlier than `checkin` date.

## C338 — Create Booking accepts invalid data types

**Priority:** High  
**Type:** Functional  

### Preconditions

1. Postman is opened.
2. Postman environment is selected.
3. baseUrl is set to https://restful-booker.herokuapp.com.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a `POST` request to `{{baseUrl}}/booking`. | Request URL is prepared. |
| 2 | Set headers: `Content-Type: application/json`, `Accept: application/json`. | Headers are added. |
| 3 | Add booking data with invalid data types: `totalprice` as string and `depositpaid` as string. | Request body contains invalid data types. |
| 4 | Send the request. | API should return `400 Bad Request` with validation error and booking should not be created. |

**Known Issue:** API returns `200 OK`, creates a booking, saves invalid `totalprice` as `null`, and converts invalid `depositpaid` string value to `true`.
