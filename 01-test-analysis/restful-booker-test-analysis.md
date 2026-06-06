# Test Analysis – Restful Booker API

## Application Under Test

Restful Booker API is a demo REST API for booking management.

API documentation:
https://restful-booker.herokuapp.com/apidoc/index.html

## Testing Scope

The testing scope includes:

- Authentication
- Booking creation
- Booking retrieval
- Booking update
- Partial booking update
- Booking deletion
- Positive and negative API scenarios
- Basic response validation
- Status code validation
- Response body validation

## Features / Endpoints in Scope

| Feature | Method | Endpoint |
|---|---|---|
| Create token | POST | /auth |
| Get booking IDs | GET | /booking |
| Get booking by ID | GET | /booking/{id} |
| Create booking | POST | /booking |
| Update booking | PUT | /booking/{id} |
| Partial update booking | PATCH | /booking/{id} |
| Delete booking | DELETE | /booking/{id} |

## Out of Scope

The following areas were not included in the testing scope because they are not relevant or not available for this project setup:

| Area | Reason |
|---|---|
| UI testing | Restful Booker is an API testing project. No UI flow was tested in this scope. |
| Database testing | Direct database access is not available for the public demo API. |
| Performance/load testing | The project focuses on functional API testing. Load testing requires a separate setup and is outside the current scope. |
| Security penetration testing | Only basic authorization checks were performed. Full security testing requires a separate security-focused scope. |
| Automation framework implementation | Tests were automated using Postman assertions and Newman runs, but no separate code-based automation framework was implemented. |
| Real payment or external service integrations | Restful Booker does not include real payment processing or external service integrations. |

## Test Data

### Valid Auth Data

| Field | Value |
|---|---|
| username | admin |
| password | password123 |

### Valid Booking Data

| Field | Example |
|---|---|
| firstname | Harry |
| lastname | Potter |
| totalprice | 150 |
| depositpaid | true |
| checkin | 2026-07-11 |
| checkout | 2026-07-15 |
| additionalneeds | Breakfast |

### Update Booking Data

| Field | Example |
|---|---|
| firstname | Ron |
| lastname | Weasley |
| totalprice | 200 |
| depositpaid | false |
| checkin | 2026-08-01 |
| checkout | 2026-08-05 |
| additionalneeds | Dinner |

### Partial Update Data

| Field | Example |
|---|---|
| firstname | Hermione |
| additionalneeds | Late checkout |

### Invalid / Bug-Related Data

| Scenario | Example |
|---|---|
| Missing required field | `totalprice` is not sent |
| Invalid data types | `totalprice: "abc"`, `depositpaid: "no"` |
| Invalid date range | `checkin: 2026-07-21`, `checkout: 2026-07-11` |
| Checkin filter boundary | booking checkin equals filter checkin |

## Test Design Approach

### Positive Scenarios

- Create token with valid credentials
- Create booking with valid body
- Get booking by valid ID
- Get all booking IDs
- Filter booking IDs by firstname and lastname
- Filter booking IDs by checkin and checkout dates
- Verify deleted booking is no longer available
- Update booking with valid token
- Partially update booking with valid token
- Delete booking with valid token

### Negative Scenarios

- Create token with invalid credentials
- Create token with empty request body
- Get booking by non-existing ID
- Filter bookings by non-existing firstname/lastname
- Create booking without required `totalprice` field
- Create booking with invalid data types
- Create booking with checkout date earlier than checkin date
- Update booking without authorization
- Update booking with invalid booking ID
- Partial update booking without authorization
- Delete booking without authorization
- Verify that deleted booking is not accessible
- Verify checkin date filter boundary behavior

## Risks

| Risk | Description |
|---|---|
| Invalid authentication handling | API may allow protected actions without valid token |
| Incorrect status codes | API may return incorrect HTTP status codes |
| Missing validation | API may accept incomplete or invalid request bodies |
| Data inconsistency | Created or updated booking data may not match request body |
| Delete behavior issue | Deleted booking may still be accessible after DELETE request |
| Incorrect filtering logic | API may return incorrect booking IDs when filtering by checkin or checkout dates |

## Acceptance Criteria

- API returns expected HTTP status codes
- Response body contains required fields
- Created booking can be retrieved by ID
- Updated booking reflects changed data
- Protected endpoints require valid authentication
- Invalid requests are handled with appropriate errors
- Booking filters return relevant booking IDs according to query parameters
- Deleted booking is not available by ID after successful deletion
- Invalid or incomplete request bodies are rejected with client-side error status codes
