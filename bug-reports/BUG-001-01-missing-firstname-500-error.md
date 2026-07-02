# BUG-001-01: Missing firstname Field Returns 500 Internal Server Error on POST /booking

**Bug ID:** BUG-001-01
**Endpoint:** POST /booking
**Severity:** High
**Priority:** High
**Status:** Open
**Reproducibility:** Intermittent
**Reported By:** Felicia Agbooluchi
**Date:** June 2026

---

## Summary

When the firstname field is omitted from the POST /booking request body, the API returns a 500 Internal Server Error instead of a 400 Bad Request. The server crashes rather than returning a proper validation error.

---

## Environment

| Component | Details |
|---|---|
| API | Restful-Booker |
| URL | https://restful-booker.herokuapp.com |
| Tool | Postman |
| Browser | Chrome 149.0.7827.115 (64-bit) |
| Device | HP EliteBook 840 G3 |
| Network | WiFi |

---

## Preconditions

API is accessible at https://restful-booker.herokuapp.com

---

## Steps to Reproduce

1. Open Postman
2. Send a POST request to https://restful-booker.herokuapp.com/booking
3. Set Content-Type to application/json
4. Include all required fields in the request body EXCEPT firstname
5. Observe the response

**Request Body:**
```json
{
  "lastname": "Test",
  "totalprice": 200,
  "depositpaid": true,
  "bookingdates": {
    "checkin": "2026-07-01",
    "checkout": "2026-07-05"
  }
}
```

---

## Expected Result

400 Bad Request with a validation error message indicating firstname is required.

---

## Actual Result

500 Internal Server Error. The server crashes instead of returning a validation error.

---

## Evidence

![Screenshot](screenshots/BUG-001-01-screenshot.jpeg)

---

## Impact

The server exposes a 500 error to the client instead of handling missing fields gracefully. In a production environment, this indicates the API has no server-side validation for required fields and is vulnerable to crashes from malformed requests.
