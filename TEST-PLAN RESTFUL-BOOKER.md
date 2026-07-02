# Restful-Booker API Test Plan

**Project:** Manual API Testing of Restful-Booker
**Tester:** Felicia Agbooluchi
**Date:** June 2026
**Version:** 1.0

---

## 1. Introduction

### Objective
Validate core API functionality, negative paths, and edge cases of the Restful-Booker API — a hotel booking REST API playground available at https://restful-booker.herokuapp.com.

### Scope
- Authentication (token generation via POST /auth)
- POST /booking (create booking)
- GET /booking (retrieve all bookings and single booking by ID)
- PUT /booking/{id} (full update)
- PATCH /booking/{id} (partial update)
- DELETE /booking/{id} (delete booking)

Includes positive testing, negative testing, field validation, data type validation, and authentication testing.

### Out of Scope
- Performance load testing
- Security penetration testing
- UI testing
- Database testing

---

## 2. Test Environment

| Component | Details |
|---|---|
| API URL | https://restful-booker.herokuapp.com |
| Tool | Postman |
| Browser | Chrome 149.0.7827.115 (64-bit) |
| Device | HP EliteBook 840 G3 |
| Network | WiFi |

---

## 3. Test Data Summary

| Field | Valid Data | Invalid Data | Observed Behaviour |
|---|---|---|---|
| firstname | "Felicia" | "1234567", "" | Valid creates booking; invalid should reject but doesn't |
| lastname | "Test" | "%%%132", "" | Valid creates booking; invalid should reject but doesn't |
| totalprice | 200 | "high", "" | Valid creates booking; invalid correctly rejected |
| depositpaid | true | "Good", "" | Valid creates booking; invalid correctly rejected |
| checkin | "2026-07-01" | "notadate", "" | Valid creates booking; invalid should reject but doesn't |
| checkout | "2026-07-05" | "notadate", "" | Valid creates booking; invalid should reject but doesn't |
| Auth credentials | username: admin / password: password123 | Modified token string | Valid generates token; invalid returns 403 |

---

## 4. Entry and Exit Criteria

### Entry Criteria
- Restful-Booker API is accessible
- Postman is installed and configured
- Valid auth credentials are available (admin/password123)
- No blocking defects on the authentication endpoint

### Exit Criteria
- All High priority test cases executed and results documented
- Medium priority tests executed with known issues logged
- All bugs logged with steps to reproduce, expected and actual results
- At least one full test cycle completed across all endpoints

---

## 5. Risks and Limitations

| Risk | Impact | Mitigation |
|---|---|---|
| API resets every 10 minutes | Booking IDs become invalid; some bugs may be intermittent | Generate fresh token and booking ID before each test session |
| Public sandbox environment | Results may vary across sessions | Re-run failing tests multiple times to confirm reproducibility |
| No persistent data | Cannot test long-term data integrity | Accepted as a known limitation of the test environment |

---

## 6. Testing Techniques Used

| Technique | Description |
|---|---|
| Positive testing | Verified all endpoints work correctly with valid data and valid auth tokens |
| Negative testing | Tested missing required fields, empty field values, and invalid data types |
| Data type validation | Verified that fields reject incorrect data types (numeric strings in name fields, invalid date formats) |
| Authentication testing | Verified that protected endpoints reject requests with no token and invalid tokens |
| Error code validation | Verified that API returns correct HTTP status codes for non-existent resource IDs |

---

## 7. Test Coverage

| Endpoint | Test Cases | Focus |
|---|---|---|
| POST /booking | TC-POST-001 to TC-POST-019 | Valid creation, missing fields, empty fields, invalid data types |
| GET /booking | TC-GET-001 to TC-GET-005 | Retrieve all bookings, valid ID, non-existent ID, string ID, negative ID |
| PUT /booking/{id} | TC-PUT-001 to TC-PUT-004 | Valid update, no token, invalid token, non-existent ID |
| PATCH /booking/{id} | TC-PATCH-001 to TC-PATCH-004 | Partial update, no token, invalid token, non-existent ID |
| DELETE /booking/{id} | TC-DEL-001 to TC-DEL-004 | Valid delete, no token, invalid token, non-existent ID |

---

## 8. Deliverables

- Test plan (this document)
- Executed test cases ([TEST-CASES.md](./TEST-CASES.md))
- Bug reports ([bug-reports/README.md](./bug-reports/README.md))
- Bug report screenshots ([bug-reports/screenshots/](./bug-reports/screenshots/))
- Test execution summary (included in TEST-CASES.md)

---

## 9. Test Execution Summary

| Endpoint | Total | Pass | Fail |
|---|---|---|---|
| POST | 19 | 5 | 14 |
| GET | 5 | 5 | 0 |
| PUT | 4 | 3 | 1 |
| PATCH | 4 | 3 | 1 |
| DELETE | 4 | 3 | 1 |
| **Total** | **36** | **19** | **17** |
