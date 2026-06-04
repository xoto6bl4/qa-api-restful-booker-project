# Booking API - PUT/PATCH Test Cases

## Test Environment

- **API:** Restful Booker
- **Base URL:** `https://restful-booker.herokuapp.com`
- **Tool:** Postman
- **OS:** Windows 11
- **Environment:** Restful Booker Environment

## Test Cases Summary

| ID | Title | Priority | Type |
|---|---|---|---|
| C330 | Update booking with token | High | Functional |
| C331 | Update without authorization | High | Security |
| C332 | Update non-existing ID | Medium | Functional |
| C333 | Partially update firstname with token | High | Functional |
| C334 | Partial update without authorization | High | Security |

## C330 — Update booking with token

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
| 1 | Create a PUT request to {{baseUrl}}/booking/{{bookingId}}. | Request URL is prepared with valid booking ID. |
| 2 | Set headers: Content-Type: application/json, Accept: application/json, Cookie: token={{token}}. | Headers are added with valid token. |
| 3 | Add valid updated booking data in request body. | Request body contains valid updated data. |
| 4 | Send the request. | API returns 200 OK and response contains updated booking object. |

## C331 — Update without authorization

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
| 1 | Create a PUT request to {{baseUrl}}/booking/{{bookingId}}. | Request URL is prepared with valid booking ID. |
| 2 | Set headers: Content-Type: application/json, Accept: application/json. | Headers are added without authorization token. |
| 3 | Add valid updated booking data in request body. | Request body contains valid updated data. |
| 4 | Send the request. | API returns 403 Forbidden and response indicates forbidden access. |

## C332 — Update non-existing ID

**Priority:** Medium  
**Type:** Functional  

### Preconditions

1. Postman is opened.
2. Postman environment is selected.
3. baseUrl is set to https://restful-booker.herokuapp.com.
4. A valid token is generated.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a PUT request to {{baseUrl}}/booking/999999999. | Request URL contains non-existing booking ID. |
| 2 | Set headers: Content-Type: application/json, Accept: application/json, Cookie: token={{token}}. | Headers are added with valid token. |
| 3 | Add valid updated booking data in request body. | Request body contains valid updated data. |
| 4 | Send the request. | API returns 405 Method Not Allowed. |

## C333 — Partially update firstname with token

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
| 1 | Create a PATCH request to {{baseUrl}}/booking/{{bookingId}}. | Request URL is prepared with valid booking ID. |
| 2 | Set headers: Content-Type: application/json, Accept: application/json, Cookie: token={{token}}. | Headers are added with valid token. |
| 3 | Add request body with only firstname changed. | Request body contains partial update data. |
| 4 | Send the request. | API returns 200 OK. firstname is updated. Fields not included in PATCH request remain unchanged. |

## C334 — Partial update without authorization

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
| 1 | Create a PATCH request to {{baseUrl}}/booking/{{bookingId}}. | Request URL is prepared with valid booking ID. |
| 2 | Set headers: Content-Type: application/json, Accept: application/json. | Headers are added without authorization token. |
| 3 | Add valid partial update data in request body. | Request body contains valid partial update data. |
| 4 | Send the request. | API returns 403 Forbidden. Response indicates forbidden access. |
