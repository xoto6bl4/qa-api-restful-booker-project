# Restful Booker API Checklist

## Project Information

- **Application:** Restful Booker API
- **Base URL:** `https://restful-booker.herokuapp.com`
- **Tool:** Postman
- **Runner:** Newman
- **Test Management:** TestRail
- **Bug Tracking:** Jira

---

## Auth API

- [x] Verify token is created with valid credentials.
- [x] Verify response contains `token` after successful authentication.
- [x] Verify invalid credentials do not return a token.
- [x] Verify invalid credentials return `Bad credentials` reason.
- [x] Verify empty request body does not return a token.
- [x] Verify empty request body returns `Bad credentials` reason.

---

## Booking API - GET

- [x] Verify all booking IDs can be retrieved.
- [x] Verify response for all booking IDs is an array.
- [x] Verify each returned item contains `bookingid`.
- [x] Verify booking IDs can be filtered by `firstname` and `lastname`.
- [x] Verify booking IDs can be filtered by `checkin` and `checkout` dates.
- [x] Verify filter with non-existing name returns an empty array.
- [x] Verify booking can be retrieved by valid booking ID.
- [x] Verify retrieved booking contains correct personal data.
- [x] Verify retrieved booking contains correct booking dates.
- [x] Verify retrieved booking contains correct additional needs.
- [x] Verify non-existing booking ID returns an error response.

---

## Booking API - POST

- [x] Verify booking can be created with valid data.
- [x] Verify response contains `bookingid` after successful booking creation.
- [x] Verify created booking response contains correct personal data.
- [x] Verify created booking response contains correct price and deposit status.
- [x] Verify created booking response contains correct checkin and checkout dates.
- [x] Verify created booking response contains correct additional needs.
- [x] Verify booking creation without required `totalprice` field is handled.
- [x] Verify booking creation with invalid data types is handled.
- [x] Verify booking creation with checkout date earlier than checkin date is handled.

---

## Booking API - PUT / PATCH

- [x] Verify booking can be fully updated with a valid token.
- [x] Verify updated booking response contains changed personal data.
- [x] Verify updated booking response contains changed price and deposit status.
- [x] Verify updated booking response contains changed booking dates.
- [x] Verify updated booking response contains changed additional needs.
- [x] Verify booking update without authorization is rejected.
- [x] Verify booking update with non-existing booking ID is handled.
- [x] Verify booking can be partially updated with a valid token.
- [x] Verify partial update changes only provided fields.
- [x] Verify unchanged fields remain the same after partial update.
- [x] Verify partial update without authorization is rejected.

---

## Booking API - DELETE

- [x] Verify booking can be deleted with a valid token.
- [x] Verify delete request without authorization is rejected.
- [x] Verify deleted booking is no longer accessible by ID.
- [x] Verify deleted booking returns `404 Not Found` when requested again.

---

## Negative Testing

- [x] Verify auth with invalid credentials.
- [x] Verify auth with empty body.
- [x] Verify get booking by non-existing ID.
- [x] Verify filtering by non-existing name.
- [x] Verify update booking without authorization.
- [x] Verify update booking with invalid booking ID.
- [x] Verify partial update without authorization.
- [x] Verify delete booking without authorization.
- [x] Verify booking creation with missing required field.
- [x] Verify booking creation with invalid data types.
- [x] Verify booking creation with invalid date range.

---

## Bug Evidence Checklist

- [x] Verify API returns `500 Internal Server Error` instead of a client-side validation error when `totalprice` is missing.
- [x] Verify API accepts invalid data types for `totalprice` and `depositpaid`.
- [x] Verify API creates a booking when checkout date is earlier than checkin date.
- [x] Verify API checkin date filter does not return a booking when filter checkin date equals booking checkin date.
- [x] Verify bug-related requests are separated from the main positive and negative scenarios.
- [x] Verify bug evidence is documented in Jira bug reports.
- [x] Verify failed bug-related test cases are linked to Jira defects in TestRail.

---

## Test Evidence

- [x] Postman collection is created.
- [x] Postman environment is created.
- [x] Main Newman run is executed.
- [x] Main Newman run has 0 failed tests.
- [x] Bug evidence Newman run is executed separately.
- [x] TestRail test run is executed.
- [x] Failed TestRail cases are linked to Jira defects.
- [x] Test run screenshots are added to the repository.
- [x] Bug reports are added to the repository.

---

## Notes

The checklist covers the main Restful Booker API flows, including authentication, CRUD operations, filtering, authorization checks, negative scenarios, and documented API defects.

Bug-related checks are intentionally included because they confirm known issues found during testing.
