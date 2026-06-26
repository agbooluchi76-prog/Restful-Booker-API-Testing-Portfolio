# Restful-Booker API Test Cases

**Application:** [Restful-Booker API](https://restful-booker.herokuapp.com)
**Tester:** Felicia Agbooluchi
**Date:** June 2026
**Total Test Cases:** 36 | **Pass:** 19 | **Fail:** 17

---

## POST /booking

| TC ID | Description | Preconditions | Test Data | Steps | Expected Result | Actual Result | Status |
|---|---|---|---|---|---|---|---|
| TC-POST-001 | Create booking with valid data | API is accessible | All fields valid | Send POST /booking with all valid fields | 200 OK, booking created with bookingid | 200 OK, booking created | Pass |
| TC-POST-002 | Create booking with missing firstname | API is accessible | All fields valid except firstname removed | Send POST /booking without firstname | 400 Bad Request | 500 Internal Server Error | **Fail** |
| TC-POST-003 | Create booking with missing lastname | API is accessible | All fields valid except lastname removed | Send POST /booking without lastname | 400 Bad Request | 500 Internal Server Error | **Fail** |
| TC-POST-004 | Create booking with missing totalprice | API is accessible | All fields valid except totalprice removed | Send POST /booking without totalprice | 400 Bad Request | 500 Internal Server Error | **Fail** |
| TC-POST-005 | Create booking with missing depositpaid | API is accessible | All fields valid except depositpaid removed | Send POST /booking without depositpaid | 400 Bad Request | 500 Internal Server Error | **Fail** |
| TC-POST-006 | Create booking with missing checkin | API is accessible | All fields valid except checkin removed | Send POST /booking without checkin | 400 Bad Request | 500 Internal Server Error | **Fail** |
| TC-POST-007 | Create booking with missing checkout | API is accessible | All fields valid except checkout removed | Send POST /booking without checkout | 400 Bad Request | 500 Internal Server Error | **Fail** |
| TC-POST-008 | Create booking with empty firstname | API is accessible | firstname set to "" | Send POST /booking with firstname as empty string | 400 Bad Request | 200 OK, booking created | **Fail** |
| TC-POST-009 | Create booking with empty lastname | API is accessible | lastname set to "" | Send POST /booking with lastname as empty string | 400 Bad Request | 200 OK, booking created | **Fail** |
| TC-POST-010 | Create booking with empty totalprice | API is accessible | totalprice set to "" | Send POST /booking with totalprice as empty string | 400 Bad Request | 400 Bad Request | Pass |
| TC-POST-011 | Create booking with empty depositpaid | API is accessible | depositpaid set to "" | Send POST /booking with depositpaid as empty string | 400 Bad Request | 400 Bad Request | Pass |
| TC-POST-012 | Create booking with empty checkin | API is accessible | checkin set to "" | Send POST /booking with checkin as empty string | 400 Bad Request | 200 OK, booking created | **Fail** |
| TC-POST-013 | Create booking with empty checkout | API is accessible | checkout set to "" | Send POST /booking with checkout as empty string | 400 Bad Request | 200 OK, booking created | **Fail** |
| TC-POST-014 | Create booking with number as firstname | API is accessible | firstname set to "1234567" | Send POST /booking with firstname as numeric string | 400 Bad Request | 200 OK, booking created | **Fail** |
| TC-POST-015 | Create booking with special characters as lastname | API is accessible | lastname set to "%%%132" | Send POST /booking with lastname as special characters | 400 Bad Request | 200 OK, booking created | **Fail** |
| TC-POST-016 | Create booking with string as totalprice | API is accessible | totalprice set to "high" | Send POST /booking with totalprice as string | 400 Bad Request | 400 Bad Request | Pass |
| TC-POST-017 | Create booking with string as depositpaid | API is accessible | depositpaid set to "Good" | Send POST /booking with depositpaid as string | 400 Bad Request | 400 Bad Request | Pass |
| TC-POST-018 | Create booking with invalid date as checkin | API is accessible | checkin set to "notadate" | Send POST /booking with checkin as invalid date | 400 Bad Request | 200 OK, booking created | **Fail** |
| TC-POST-019 | Create booking with invalid date as checkout | API is accessible | checkout set to "notadate" | Send POST /booking with checkout as invalid date | 400 Bad Request | 200 OK, booking created | **Fail** |

---

## GET /booking

| TC ID | Description | Preconditions | Test Data | Steps | Expected Result | Actual Result | Status |
|---|---|---|---|---|---|---|---|
| TC-GET-001 | Get all bookings | API is accessible | None | Send GET /booking | 200 OK with list of booking IDs | 200 OK with list of booking IDs | Pass |
| TC-GET-002 | Get single booking with valid ID | API is accessible, booking exists | Valid booking ID | Send GET /booking/{valid ID} | 200 OK with booking data | 200 OK with booking data | Pass |
| TC-GET-003 | Get booking with non-existent ID | API is accessible | ID: 657498 | Send GET /booking/657498 | 404 Not Found | 404 Not Found | Pass |
| TC-GET-004 | Get booking with string ID | API is accessible | ID: acgbdh | Send GET /booking/acgbdh | 404 Not Found | 404 Not Found | Pass |
| TC-GET-005 | Get booking with negative ID | API is accessible | ID: -123 | Send GET /booking/-123 | 404 Not Found | 404 Not Found | Pass |

---

## PUT /booking/{id}

| TC ID | Description | Preconditions | Test Data | Steps | Expected Result | Actual Result | Status |
|---|---|---|---|---|---|---|---|
| TC-PUT-001 | Full update with valid token and valid ID | API accessible, valid token, booking exists | Valid token, valid ID, full body | Send PUT /booking/{valid ID} with all fields and valid token | 200 OK with updated booking data | 200 OK with updated booking data | Pass |
| TC-PUT-002 | Full update with no token | API accessible, booking exists | No token, valid ID, full body | Send PUT /booking/{valid ID} with no authorization | 403 Forbidden | 403 Forbidden | Pass |
| TC-PUT-003 | Full update with invalid token | API accessible, booking exists | Invalid token, valid ID, full body | Send PUT /booking/{valid ID} with invalid token | 403 Forbidden | 403 Forbidden | Pass |
| TC-PUT-004 | Full update with non-existent ID | API accessible, valid token | Valid token, ID: 1309999, full body | Send PUT /booking/1309999 with valid token | 404 Not Found | 405 Method Not Allowed | **Fail** |

---

## PATCH /booking/{id}

| TC ID | Description | Preconditions | Test Data | Steps | Expected Result | Actual Result | Status |
|---|---|---|---|---|---|---|---|
| TC-PATCH-001 | Partial update with valid token and valid ID | API accessible, valid token, booking exists | Valid token, valid ID, firstname and lastname only | Send PATCH /booking/{valid ID} with partial body and valid token | 200 OK with updated fields | 200 OK with updated data | Pass |
| TC-PATCH-002 | Partial update with no token | API accessible, booking exists | No token, valid ID | Send PATCH /booking/{valid ID} with no authorization | 403 Forbidden | 403 Forbidden | Pass |
| TC-PATCH-003 | Partial update with invalid token | API accessible, booking exists | Invalid token, valid ID | Send PATCH /booking/{valid ID} with invalid token | 403 Forbidden | 403 Forbidden | Pass |
| TC-PATCH-004 | Partial update with non-existent ID | API accessible, valid token | Valid token, ID: 2130000000 | Send PATCH /booking/2130000000 with valid token | 404 Not Found | 403 Forbidden | **Fail** |

---

## DELETE /booking/{id}

| TC ID | Description | Preconditions | Test Data | Steps | Expected Result | Actual Result | Status |
|---|---|---|---|---|---|---|---|
| TC-DEL-001 | Delete booking with valid token and valid ID | API accessible, valid token, booking exists | Valid token, valid ID | Send DELETE /booking/{valid ID} with valid token | 200 OK or 204 No Content | 201 Created | Pass |
| TC-DEL-002 | Delete booking with no token | API accessible, booking exists | No token, valid ID | Send DELETE /booking/{valid ID} with no authorization | 403 Forbidden | 403 Forbidden | Pass |
| TC-DEL-003 | Delete booking with invalid token | API accessible, booking exists | Invalid token, valid ID | Send DELETE /booking/{valid ID} with invalid token | 403 Forbidden | 403 Forbidden | Pass |
| TC-DEL-004 | Delete booking with non-existent ID | API accessible, valid token | Valid token, ID: 1523333333333 | Send DELETE /booking/1523333333333 with valid token | 404 Not Found | 405 Method Not Allowed | **Fail** |

---

## Test Execution Summary

| Endpoint | Total | Pass | Fail |
|---|---|---|---|
| POST /booking | 19 | 5 | 14 |
| GET /booking | 5 | 5 | 0 |
| PUT /booking/{id} | 4 | 3 | 1 |
| PATCH /booking/{id} | 4 | 3 | 1 |
| DELETE /booking/{id} | 4 | 3 | 1 |
| **Total** | **36** | **19** | **17** |
