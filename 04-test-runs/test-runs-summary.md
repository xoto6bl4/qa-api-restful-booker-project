# Test Run Summary – Restful Booker API

## Test Run

**Restful Booker API Test Run**

## Scope

- Authentication
- Booking creation
- Booking retrieval
- Booking filtering
- Booking update
- Partial booking update
- Booking deletion
- Positive API scenarios
- Negative API scenarios
- Bug evidence scenarios

## Test Environment

- **Application:** Restful Booker API
- **API Base URL:** `https://restful-booker.herokuapp.com`
- **Tool:** Postman
- **CLI Runner:** Newman
- **Test Management:** TestRail
- **Bug Tracking:** Jira
- **OS:** Windows 11
- **Tester:** Amal Kamalov
- **Test Date:** 04/06/2026

---

## Newman Main Run

Main Newman run includes positive and negative API scenarios without known bug evidence requests.

| Metric | Count |
|---|---:|
| Total requests | 18 |
| Total assertions | 62 |
| Failed tests | 0 |
| Skipped tests | 0 |

![Newman main run summary](screenshots/newman-main-run-summary.png)

[Full Newman Main Run Report](newman-test-run/newman-main-run-report.html)

---

## Newman Bug Evidence Run

Bug evidence run includes requests from the `Bug Candidates / Known Issues` folder.

Failed assertions are expected because these tests validate correct expected behavior against known API defects.

| Metric | Count |
|---|---:|
| Total requests | 7 |
| Total assertions | 12 |
| Failed tests | 6 |
| Skipped tests | 0 |

![Newman bug evidence run summary](screenshots/newman-bug-evidence-summary.png)

[Full Newman Bug Evidence Report](newman-test-run/newman-bug-evidence-report.html)

---

## TestRail Run Summary

| Status | Count | Percentage |
|---|---:|---:|
| Passed | 18 | 82% |
| Failed | 4 | 18% |
| Blocked | 0 | 0% |
| Skipped | 0 | 0% |
| **Total** | **22** | **100%** |

![TestRail run summary](screenshots/testrail-run-summary.png)

---

## Defects Found

| Bug ID | Summary | Priority | Related Test Case | Jira Issue |
|---|---|---|---|---|
| BUG-001 | API returns `500 Internal Server Error` when creating booking without required `totalprice` field | Medium | C328 | QSD-10 |
| BUG-002 | API creates booking with invalid data types for `totalprice` and `depositpaid` | Medium | C338 | QSD-11 |
| BUG-003 | API creates booking when checkout date is earlier than checkin date | Medium | C329 | QSD-13 |
| BUG-004 | API date filter does not return booking when checkin filter equals booking checkin date | Medium | C339 | QSD-14 |

---

## TestRail Export

| File | Description |
|---|---|
| [testrail-run-results.csv](testrail-test-run/testrail-run-results.csv) | Exported TestRail run results with statuses, comments, priorities, types, and linked Jira defects |
| [testrail-run-stats.csv](testrail-test-run/testrail-run-stats.csv) | TestRail run status statistics |

---

## Summary

The executed test run covered the main Restful Booker API flows: authentication, booking CRUD operations, filtering, authorization checks, and negative validation scenarios.

The main Newman run passed successfully with **62/62 assertions passed**.

The TestRail run contains **18 passed** and **4 failed** test cases. Failed cases are linked to documented Jira defects and represent confirmed API validation/filtering issues.

The bug evidence Newman run was executed separately to demonstrate known API defects with reproducible failed assertions.
