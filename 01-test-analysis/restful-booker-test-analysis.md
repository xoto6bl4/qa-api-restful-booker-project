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

- UI testing
- Database testing
- Performance/load testing
- Security penetration testing
- Automation framework implementation
- Real payment or external service integrations

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

## Test Design Approach

### Positive Scenarios

- Create token with valid credentials
- Create booking with valid body
- Get booking by valid ID
- Update booking with valid token
- Partially update booking with valid token
- Delete booking with valid token

### Negative Scenarios

- Create token with invalid credentials
- Get booking by invalid ID
- Create booking with missing required fields
- Update booking without token
- Update booking with invalid token
- Delete booking without token
- Delete booking with invalid booking ID

## Risks

| Risk | Description |
|---|---|
| Invalid authentication handling | API may allow protected actions without valid token |
| Incorrect status codes | API may return incorrect HTTP status codes |
| Missing validation | API may accept incomplete or invalid request bodies |
| Data inconsistency | Created or updated booking data may not match request body |
| Delete behavior issue | Deleted booking may still be accessible after DELETE request |

## Acceptance Criteria

- API returns expected HTTP status codes
- Response body contains required fields
- Created booking can be retrieved by ID
- Updated booking reflects changed data
- Protected endpoints require valid authentication
- Invalid requests are handled with appropriate errors
