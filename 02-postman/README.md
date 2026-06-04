# Postman Collection

This folder contains the Postman collection and environment used for API testing of the Restful Booker API.

## Technologies Used

- **Tool:** Postman
- **CLI Runner:** Newman
- **API Type:** RESTful API
- **Testing Scope:** CRUD, authentication, filtering, validation
- **Techniques:** Environment variables, collection variables, automated assertions, negative testing
- **Reports:** Newman HTML reports

## Files

| File                                                                                                       | Description                                                               |
| ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| [restful-booker-api-tests.postman_collection.json](01-QA-API-Restful-Booker-Project.postman_collection.json)       | Postman collection with positive, negative, and bug-related API scenarios |
| [restful-booker-environment.postman_environment.json](02-Restful-Booker-Environment.postman_environment.json) | Postman environment with base URL and runtime variables                   |

## Collection Structure

The collection is divided into three main folders:

* `Positive Scenarios` — valid API flows and successful CRUD operations
* `Negative Scenarios` — invalid or unauthorized API requests
* `Bug Candidates / Known Issues` — requests used as evidence for documented API defects

## How to Run

### Option 1: Run in Postman

1. Import the collection into Postman.
2. Import the environment file.
3. Select `Restful Booker Environment`.
4. Run `Positive Scenarios` and `Negative Scenarios` for the main test run.
5. Run `Bug Candidates / Known Issues` separately for bug evidence.

### Option 2: Run via Newman CLI

Run the collection from the command line:

```bash
newman run restful-booker-api-tests.postman_collection.json -e restful-booker-environment.postman_environment.json
```

To generate an HTML report:

```bash
newman run restful-booker-api-tests.postman_collection.json -e restful-booker-environment.postman_environment.json -r htmlextra
```

## Notes

The `Bug Candidates / Known Issues` folder contains deliberate test failures that expose actual API defects, such as:

* API accepts invalid data types, for example string values in numeric or boolean fields.
* API creates bookings with invalid date logic, for example checkout date earlier than checkin date.
* API returns `500 Internal Server Error` instead of a client-side validation error when a required field is missing.
* API checkin date filter does not return a booking when the filter date matches the booking checkin date.

Detailed bug reports can be found in the [`05-bug-reports`](../05-bug-reports) folder.
