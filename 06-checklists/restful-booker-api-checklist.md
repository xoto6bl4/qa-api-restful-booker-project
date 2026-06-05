# Restful Booker API Checklist

## Auth API

* [x] Verify token is created with valid credentials
* [x] Verify token is not returned with invalid credentials
* [x] Verify token is not returned with empty request body
* [x] Verify error response is returned for invalid authentication data

## Booking API - GET

* [x] Verify all booking IDs can be retrieved
* [x] Verify response from `GET /booking` is an array
* [x] Verify each booking list item contains `bookingid`
* [x] Verify booking can be retrieved by valid ID
* [x] Verify booking data returned by ID matches created booking data
* [x] Verify non-existing booking ID returns error response
* [x] Verify booking IDs can be filtered by firstname and lastname
* [x] Verify booking IDs can be filtered by checkin and checkout dates
* [x] Verify non-existing name filter returns empty array

## Booking API - POST

* [x] Verify booking can be created with valid data
* [x] Verify created booking response contains `bookingid`
* [x] Verify created booking response contains correct firstname and lastname
* [x] Verify created booking response contains correct total price
* [x] Verify created booking response contains correct deposit status
* [x] Verify created booking response contains correct checkin and checkout dates
* [x] Verify created booking response contains correct additional needs
* [x] Verify booking creation without required `totalprice` field
* [x] Verify booking creation with invalid data types
* [x] Verify booking creation with checkout date earlier than checkin date

## Booking API - PUT

* [x] Verify booking can be fully updated with valid token
* [x] Verify updated booking response contains changed firstname and lastname
* [x] Verify updated booking response contains changed total price
* [x] Verify updated booking response contains changed deposit status
* [x] Verify updated booking response contains changed checkin and checkout dates
* [x] Verify updated booking response contains changed additional needs
* [x] Verify booking update without authorization is rejected
* [x] Verify booking update with non-existing booking ID is handled correctly

## Booking API - PATCH

* [x] Verify booking can be partially updated with valid token
* [x] Verify partial update changes only provided fields
* [x] Verify unchanged fields remain the same after partial update
* [x] Verify partial update without authorization is rejected

## Booking API - DELETE

* [x] Verify booking can be deleted with valid token
* [x] Verify successful delete request returns expected status code
* [x] Verify delete request without authorization is rejected
* [x] Verify deleted booking is no longer accessible by ID

## Authorization Checks

* [x] Verify protected `PUT /booking/{id}` endpoint requires authorization
* [x] Verify protected `PATCH /booking/{id}` endpoint requires authorization
* [x] Verify protected `DELETE /booking/{id}` endpoint requires authorization
* [x] Verify unauthorized requests do not return booking data
* [x] Verify unauthorized requests do not return `bookingid`

## Response Validation

* [x] Verify expected HTTP status codes are returned
* [x] Verify response body structure matches expected API behavior
* [x] Verify required response fields are present
* [x] Verify response data matches request data where applicable
* [x] Verify response time is below 1000 ms for selected requests

## Bug Evidence

* [x] Verify missing required `totalprice` field returns incorrect server error
* [x] Verify API accepts invalid data types for `totalprice` and `depositpaid`
* [x] Verify API creates booking with checkout date earlier than checkin date
* [x] Verify checkin date filter does not return booking when filter date matches booking checkin date

## Coverage Summary

| Area                   | Covered |
| ---------------------- | ------- |
| Authentication         | Yes     |
| Create booking         | Yes     |
| Get booking IDs        | Yes     |
| Get booking by ID      | Yes     |
| Filter bookings        | Yes     |
| Full update booking    | Yes     |
| Partial update booking | Yes     |
| Delete booking         | Yes     |
| Authorization checks   | Yes     |
| Negative scenarios     | Yes     |
| Bug evidence scenarios | Yes     |
