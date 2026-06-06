# Restful Booker API Traceability Matrix

| Area | Endpoint | Requirement / Check | Test Case ID | Postman Request | TestRail Status | Related Bug |
|---|---|---|---|---|---|---|
| Auth | POST /auth | Token is created with valid credentials | C318 | 01 Create Token | Passed | - |
| Auth | POST /auth | Invalid credentials do not return token | C319 | 11 Create Token with Invalid Credentials | Passed | - |
| Auth | POST /auth | Empty body does not return token | C320 | 12 Create Token with empty body | Passed | - |
| Booking GET | GET /booking | All booking IDs can be retrieved | C321 | 03 Get All Booking IDs | Passed | - |
| Booking GET | GET /booking | Booking IDs can be filtered by firstname and lastname | C322 | 04 Get Booking IDs by Name Filter | Passed | - |
| Booking GET | GET /booking | Booking IDs can be filtered by checkin and checkout dates | C323 | 05 Get Booking IDs by Date Filter | Passed | - |
| Booking GET | GET /booking | Checkin filter includes booking when filter date equals booking checkin date | C339 | BUG-004 / 03 Filter Booking by matching checkin date | Failed | BUG-004 / QSD-14 |
| Booking GET | GET /booking/{id} | Booking can be retrieved by valid ID | C325 | 06 Get Created Booking | Passed | - |
| Booking GET | GET /booking/{id} | Non-existing booking ID returns error | C326 | 13 Get Booking by Invalid ID | Passed | - |
| Booking POST | POST /booking | Booking can be created with valid data | C327 | 02 Create Booking | Passed | - |
| Booking POST | POST /booking | Missing required totalprice is rejected | C328 | BUG-001 Create Booking without required totalprice returns 500 | Failed | BUG-001 / QSD-10 |
| Booking POST | POST /booking | Invalid data types are rejected | C338 | BUG-002 Create Booking accepts invalid data types | Failed | BUG-002 / QSD-11 |
| Booking POST | POST /booking | Checkout earlier than checkin is rejected | C329 | BUG-003 Create Booking with checkout earlier than checkin | Failed | BUG-003 / QSD-13 |
| Booking PUT | PUT /booking/{id} | Booking can be fully updated with token | C330 | 07 Update Booking | Passed | - |
| Booking PUT | PUT /booking/{id} | Update without authorization is rejected | C331 | 15 Update Booking Without Token | Passed | - |
| Booking PUT | PUT /booking/{id} | Update non-existing booking ID is handled | C332 | 16 Update Booking with invalid booking id | Passed | - |
| Booking PATCH | PATCH /booking/{id} | Booking can be partially updated with token | C333 | 08 Partial Update Booking | Passed | - |
| Booking PATCH | PATCH /booking/{id} | Partial update without authorization is rejected | C334 | 17 Partial update without authorization | Passed | - |
| Booking DELETE | DELETE /booking/{id} | Booking can be deleted with token | C335 | 09 Delete Booking | Passed | - |
| Booking DELETE | DELETE /booking/{id} | Delete without authorization is rejected | C336 | 18 Delete Booking Without Token | Passed | - |
| Booking DELETE | GET /booking/{id} | Deleted booking is no longer accessible | C337 | 10 Verify Deleted Booking | Passed | - |
