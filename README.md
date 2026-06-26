# Restful-Booker API Testing Portfolio

**Tester:** Felicia Agbooluchi
**Application:** [Restful-Booker API](https://restful-booker.herokuapp.com) (hotel booking REST API playground)
**Testing Period:** June 2026
**Type:** Manual API Testing
**Tool:** Postman

---

## Overview

This repository contains a complete manual API testing suite for the Restful-Booker API. All five HTTP methods were tested across authentication, booking creation, retrieval, update, and deletion flows. Positive testing, negative testing, field validation, data type validation, and authentication testing were all applied.

**36 test cases executed. 17 bugs found.**

---

## Repository Structure

```
Restful-Booker-API-Testing-Portfolio/
├── README.md               (this file)
├── TEST-PLAN.md            (test objectives, scope, environment, risks, entry/exit criteria)
├── TEST-CASES.md           (all 36 test cases with expected vs actual results)
└── bug-reports/
    ├── README.md           (bug index with severity table and links)
    ├── BUG-001-01-missing-firstname-500-error.md
    ├── BUG-001-02-missing-lastname-500-error.md
    ├── BUG-001-03-missing-totalprice-500-error.md
    ├── BUG-001-04-missing-depositpaid-500-error.md
    ├── BUG-001-05-missing-checkin-500-error.md
    ├── BUG-001-06-missing-checkout-500-error.md
    ├── BUG-002-01-empty-firstname-accepted.md
    ├── BUG-002-02-empty-lastname-accepted.md
    ├── BUG-002-03-empty-checkin-accepted.md
    ├── BUG-002-04-empty-checkout-accepted.md
    ├── BUG-003-01-numeric-string-accepted-as-firstname.md
    ├── BUG-003-02-special-chars-accepted-as-lastname.md
    ├── BUG-003-03-invalid-date-accepted-as-checkin.md
    ├── BUG-003-04-invalid-date-accepted-as-checkout.md
    ├── BUG-004-01-put-nonexistent-id-returns-405.md
    ├── BUG-005-01-patch-nonexistent-id-returns-403.md
    ├── BUG-006-01-delete-nonexistent-id-returns-405.md
    └── screenshots/
        ├── BUG-001-01-screenshot.jpeg
        ├── BUG-001-02-screenshot.jpeg
        ├── BUG-001-03-screenshot.jpeg
        ├── BUG-001-04-screenshot.jpeg
        ├── BUG-001-05-screenshot.jpeg
        ├── BUG-001-06-screenshot.jpeg
        ├── BUG-002-01-screenshot.jpeg
        ├── BUG-002-02-screenshot.jpeg
        ├── BUG-002-03-screenshot.jpeg
        ├── BUG-002-04-screenshot.jpeg
        ├── BUG-003-01-screenshot.jpeg
        ├── BUG-003-02-screenshot.jpeg
        ├── BUG-003-03-screenshot.jpeg
        ├── BUG-003-04-screenshot.jpeg
        ├── BUG-004-01-screenshot.jpeg
        ├── BUG-005-01-screenshot.jpeg
        └── BUG-006-01-screenshot.jpeg
```

---

## Test Coverage

| Endpoint | Total TCs | Pass | Fail |
|---|---|---|---|
| POST /booking | 19 | 5 | 14 |
| GET /booking | 5 | 5 | 0 |
| PUT /booking/{id} | 4 | 3 | 1 |
| PATCH /booking/{id} | 4 | 3 | 1 |
| DELETE /booking/{id} | 4 | 3 | 1 |
| **Total** | **36** | **19** | **17** |

---

## Bug Summary

| Bug ID | Title | Endpoint | Severity |
|---|---|---|---|
| [BUG-001-01](./bug-reports/BUG-001-01-missing-firstname-500-error.md) | Missing firstname field returns 500 error | POST /booking | High |
| [BUG-001-02](./bug-reports/BUG-001-02-missing-lastname-500-error.md) | Missing lastname field returns 500 error | POST /booking | High |
| [BUG-001-03](./bug-reports/BUG-001-03-missing-totalprice-500-error.md) | Missing totalprice field returns 500 error | POST /booking | High |
| [BUG-001-04](./bug-reports/BUG-001-04-missing-depositpaid-500-error.md) | Missing depositpaid field returns 500 error | POST /booking | High |
| [BUG-001-05](./bug-reports/BUG-001-05-missing-checkin-500-error.md) | Missing checkin field returns 500 error | POST /booking | High |
| [BUG-001-06](./bug-reports/BUG-001-06-missing-checkout-500-error.md) | Missing checkout field returns 500 error | POST /booking | High |
| [BUG-002-01](./bug-reports/BUG-002-01-empty-firstname-accepted.md) | Empty firstname accepted and booking created | POST /booking | High |
| [BUG-002-02](./bug-reports/BUG-002-02-empty-lastname-accepted.md) | Empty lastname accepted and booking created | POST /booking | High |
| [BUG-002-03](./bug-reports/BUG-002-03-empty-checkin-accepted.md) | Empty checkin accepted and booking created | POST /booking | High |
| [BUG-002-04](./bug-reports/BUG-002-04-empty-checkout-accepted.md) | Empty checkout accepted and booking created | POST /booking | High |
| [BUG-003-01](./bug-reports/BUG-003-01-numeric-string-accepted-as-firstname.md) | Numeric string accepted as firstname | POST /booking | High |
| [BUG-003-02](./bug-reports/BUG-003-02-special-chars-accepted-as-lastname.md) | Special characters accepted as lastname | POST /booking | High |
| [BUG-003-03](./bug-reports/BUG-003-03-invalid-date-accepted-as-checkin.md) | Invalid date string accepted as checkin | POST /booking | High |
| [BUG-003-04](./bug-reports/BUG-003-04-invalid-date-accepted-as-checkout.md) | Invalid date string accepted as checkout | POST /booking | High |
| [BUG-004-01](./bug-reports/BUG-004-01-put-nonexistent-id-returns-405.md) | PUT non-existent ID returns 405 instead of 404 | PUT /booking/{id} | Medium |
| [BUG-005-01](./bug-reports/BUG-005-01-patch-nonexistent-id-returns-403.md) | PATCH non-existent ID returns 403 instead of 404 | PATCH /booking/{id} | Medium |
| [BUG-006-01](./bug-reports/BUG-006-01-delete-nonexistent-id-returns-405.md) | DELETE non-existent ID returns 405 instead of 404 | DELETE /booking/{id} | Medium |

---

## Severity Breakdown

| Severity | Count |
|---|---|
| High | 14 |
| Medium | 3 |
| **Total** | **17** |

---

## Testing Techniques Applied

- **Positive testing** — verified all endpoints work correctly with valid data and valid auth tokens
- **Negative testing** — tested missing required fields, empty field values, and invalid data types across POST /booking
- **Data type validation** — verified that numeric strings in name fields and invalid date formats are correctly rejected
- **Authentication testing** — verified that PUT, PATCH, and DELETE endpoints reject requests with no token and with invalid tokens
- **Error code validation** — verified that correct HTTP status codes are returned for non-existent resource IDs across PUT, PATCH, and DELETE

---

## Environment

| Component | Details |
|---|---|
| API URL | https://restful-booker.herokuapp.com |
| Tool | Postman |
| Browser | Chrome 149.0.7827.115 (64-bit) |
| Device | HP EliteBook 840 G3 |
| Network | WiFi |

---

## Connect

[LinkedIn](https://www.linkedin.com/in/agbo-felicia03)
