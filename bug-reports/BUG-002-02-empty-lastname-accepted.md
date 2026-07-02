# BUG-002-02: Empty lastname Field Accepted and Booking Created on POST /booking

**Bug ID:** BUG-002-02
**Endpoint:** POST /booking
**Severity:** High
**Priority:** High
**Status:** Open
**Reproducibility:** Always
**Reported By:** Felicia Agbooluchi
**Date:** June 2026

---

## Summary

When lastname is set to an empty string, the API accepts the request and creates a booking with no lastname value.

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
4. Set lastname to an empty string ""
5. Observe the response

**Request Body:**
```json
{
  "firstname": "Felicia",
  "lastname": "",
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

400 Bad Request. Empty lastname should be rejected with a validation error.

---

## Actual Result

200 OK. Booking is created successfully with an empty lastname field.

---

## Evidence

![Screenshot](screenshots/BUG-002-02-screenshot.jpeg)

---

## Impact

Guest bookings can be created with no last name. In a production system, this would result in incomplete customer records and failed identity verification.
