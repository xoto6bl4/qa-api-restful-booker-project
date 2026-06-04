# Booking API - GET Test Cases

## Test Environment

- **API:** Restful Booker
- **Base URL:** https://restful-booker.herokuapp.com
- **Tool:** Postman
- **OS:** Windows 11
- **Environment:** Restful Booker Environment

## Test Cases Summary

| ID | Title | Priority | Type |
|---|---|---|---|
| C321 | Get all booking IDs | High | Functional |
| C322 | Filter by firstname and lastname | Medium | Functional |
| C323 | Filter by checkin / checkout dates | Medium | Functional |
| C324 | Filter with non-existing name | Low | Functional |
| C325 | Get booking by valid ID | High | Functional |
| C326 | Get booking by non-existing ID | Medium | Functional |
| C339 | Verify booking is returned when checkin filter matches booking checkin date | Medium | Functional |

## C321 — Get all booking IDs

**Priority:** High  
**Type:** Functional  

### Preconditions

- Postman is opened.
- Postman environment is selected.
- baseUrl is set to https://restful-booker.herokuapp.com.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a GET request to {{baseUrl}}/booking. | Request URL is prepared. |
| 2 | Set header Accept: application/json. | Header is added. |
| 3 | Send the request. | API returns 200 OK and response is an array. |
| 4 | Check returned items. | Each returned item contains bookingid. |

## C322 — Filter by firstname and lastname

**Priority:** Medium  
**Type:** Functional  

### Preconditions

- Postman is opened.
- Postman environment is selected.
- baseUrl is set to https://restful-booker.herokuapp.com.
- At least one booking exists with firstname and lastname used in the filter.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a GET request to {{baseUrl}}/booking. | Request URL is prepared. |
| 2 | Add query parameters: firstname=Harry, lastname=Potter. | Name filter parameters are added. |
| 3 | Set header Accept: application/json. | Header is added. |
| 4 | Send the request. | API returns 200 OK and response is an array of booking IDs matching the name filter. |
| 5 | Check returned items. | Each returned item contains bookingid. |

## C323 — Filter by checkin / checkout dates

**Priority:** Medium  
**Type:** Functional  

### Preconditions

- Postman is opened.
- Postman environment is selected.
- baseUrl is set to https://restful-booker.herokuapp.com.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a GET request to {{baseUrl}}/booking. | Request URL is prepared. |
| 2 | Add query parameters: checkin=2026-07-11, checkout=2026-07-15. | Date filter parameters are added. |
| 3 | Set header Accept: application/json. | Header is added. |
| 4 | Send the request. | API returns 200 OK and response is an array. |

## C324 — Filter with non-existing name

**Priority:** Low  
**Type:** Functional  

### Preconditions

- Postman is opened.
- Postman environment is selected.
- baseUrl is set to https://restful-booker.herokuapp.com.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a GET request to {{baseUrl}}/booking. | Request URL is prepared. |
| 2 | Add query parameters with non-existing values, for example firstname=NonExistingName, lastname=NonExistingLastName. | Non-existing name filter is added. |
| 3 | Set header Accept: application/json. | Header is added. |
| 4 | Send the request. | API returns 200 OK and response is an empty array []. |

## C325 — Get booking by valid ID

**Priority:** High  
**Type:** Functional  

### Preconditions

- Postman is opened.
- Postman environment is selected.
- baseUrl is set to https://restful-booker.herokuapp.com.
- A valid booking exists.
- bookingId variable contains a valid booking ID.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a GET request to {{baseUrl}}/booking/{{bookingId}}. | Request URL is prepared with valid booking ID. |
| 2 | Set header Accept: application/json. | Header is added. |
| 3 | Send the request. | API returns 200 OK and response contains full booking data. |

## C326 — Get booking by non-existing ID

**Priority:** Medium  
**Type:** Functional  

### Preconditions

- Postman is opened.
- Postman environment is selected.
- baseUrl is set to https://restful-booker.herokuapp.com.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a GET request to {{baseUrl}}/booking/999999999. | Request URL contains non-existing booking ID. |
| 2 | Set header Accept: application/json. | Header is added. |
| 3 | Send the request. | API returns 404 Not Found. |

## C339 — Verify booking is returned when checkin filter matches booking checkin date

**Priority:** Medium  
**Type:** Functional  

### Preconditions

- Postman is opened.
- Postman environment is selected.
- baseUrl is set to https://restful-booker.herokuapp.com.

### Steps

| Step | Step Description | Expected Result |
|---:|---|---|
| 1 | Create a POST request to {{baseUrl}}/booking with valid booking data where checkin is 2026-07-12 and checkout is 2026-07-20. | API returns 200 OK, creates a booking, and returns bookingid. |
| 2 | Send a GET request to {{baseUrl}}/booking/{bookingid}. | API returns 200 OK and the created booking contains checkin: 2026-07-12 and checkout: 2026-07-20. |
| 3 | Send a GET request to {{baseUrl}}/booking?checkin=2026-07-12&checkout=2026-07-20. | API should return 200 OK and include the created bookingid because the booking date range matches the filter values. |
| 4 | Send a GET request to {{baseUrl}}/booking?checkin=2026-07-11&checkout=2026-07-20. | API returns 200 OK and includes the created bookingid. |
