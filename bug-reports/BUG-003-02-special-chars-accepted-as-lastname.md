# BUG-003-02: Special Characters Accepted as lastname on POST /booking

**Bug ID:** BUG-003-02
**Endpoint:** POST /booking
**Severity:** High
**Priority:** High
**Status:** Open
**Reproducibility:** Always
**Reported By:** Felicia Agbooluchi
**Date:** June 2026

---

## Summary

When lastname is set to special characters such as '%%%132', the API accepts the request and creates a booking. No character validation is applied to the lastname field.

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
4. Set lastname to "%%%132"
5. Observe the response

**Request Body:**
```json
{
  "firstname": "Felicia",
  "lastname": "%%%132",
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

400 Bad Request. Special characters should be rejected in name fields.

---

## Actual Result

200 OK. Booking is created with '%%%132' as the lastname.

---

## Evidence

![Screenshot](screenshots/BUG-003-02-screenshot.jpeg)

---

## Impact

Special characters are accepted in name fields without validation. This could lead to injection vulnerabilities, corrupted records, and broken downstream systems in production.
