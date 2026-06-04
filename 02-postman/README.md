# Postman Collection

This folder contains the Postman collection and environment used for API testing of the Restful Booker API.

## Files

| File | Description |
|---|---|
| [restful-booker-api-tests.postman_collection.json](01-QA-API-Restful-Booker-Project.postman_collection.json) | Postman collection with positive, negative, and bug-related API scenarios |
| [restful-booker-environment.postman_environment.json](02-Restful-Booker-Environment.postman_environment.json) | Postman environment with base URL and runtime variables |

## Collection Structure

The collection is divided into three main folders:

- `Positive Scenarios` — valid API flows and successful CRUD operations
- `Negative Scenarios` — invalid or unauthorized API requests
- `Bug Candidates / Known Issues` — requests used as evidence for documented API defects

## How to Run

1. Import the collection into Postman.
2. Import the environment file.
3. Select `Restful Booker Environment`.
4. Run `Positive Scenarios` and `Negative Scenarios` for the main test run.
5. Run `Bug Candidates / Known Issues` separately for bug evidence.

## Notes

The bug-related folder is expected to contain failed assertions because these tests validate correct expected behavior against known API defects.
