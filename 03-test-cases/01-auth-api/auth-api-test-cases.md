# Auth API Test Cases

## Test Environment

- **API:** Restful Booker
- **Base URL:** https://restful-booker.herokuapp.com
- **Tool:** Postman
- **OS:** Windows 11
- **Environment:** Restful Booker Environment

## Test Cases Summary

| ID | Title | Priority | Type |
|---|---|---|---|
| C318 | Successful auth with valid credentials | High | Functional |
| C319 | Auth with invalid credentials | Medium | Security |
| C320 | Auth with empty body | Medium | Security |

## C318 — Successful auth with valid credentials

**Priority:** High  
**Type:** Functional  

### Preconditions

1. Postman is opened.
2. Postman environment is selected.
3. baseUrl is set to https://restful-booker.herokuapp.com.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a POST request to {{baseUrl}}/auth. | Request URL is prepared. |
| 2 | Set header Content-Type: application/json. | Header is added. |
| 3 | Add valid credentials in request body: `{ "username": "admin", "password": "password123" }`. | Request body contains valid auth data. |
| 4 | Send the request. | API returns 200 OK and response contains `token`. |

## C319 — Auth with invalid credentials

**Priority:** Medium  
**Type:** Security  

### Preconditions

1. Postman is opened.
2. Postman environment is selected.
3. baseUrl is set to https://restful-booker.herokuapp.com.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a POST request to {{baseUrl}}/auth. | Request URL is prepared. |
| 2 | Set header Content-Type: application/json. | Header is added. |
| 3 | Add invalid credentials in request body: `{ "username": "Geralt", "password": "Yennefer" }`. | Request body contains invalid auth data. |
| 4 | Send the request. | API returns 200 OK and response contains `reason: Bad credentials` and does not contain `token`. |

## C320 — Auth with empty body

**Priority:** Medium  
**Type:** Security  

### Preconditions

1. Postman is opened.
2. Postman environment is selected.
3. baseUrl is set to https://restful-booker.herokuapp.com.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a POST request to {{baseUrl}}/auth. | Request URL is prepared. |
| 2 | Set header Content-Type: application/json. | Header is added. |
| 3 | Add an empty JSON body: `{}`. | Request body is empty. |
| 4 | Send the request. | API returns 200 OK and response contains `reason: Bad credentials` and does not contain `token`. |
