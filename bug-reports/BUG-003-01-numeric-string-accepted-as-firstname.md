# BUG-003-01: Numeric String Accepted as firstname on POST /booking

**Bug ID:** BUG-003-01
**Endpoint:** POST /booking
**Severity:** High
**Priority:** High
**Status:** Open
**Reproducibility:** Always
**Reported By:** Felicia Agbooluchi
**Date:** June 2026

---

## Summary

When firstname is set to a numeric string such as '1234567', the API accepts the request and creates a booking. No data type validation is applied to the firstname field.

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
4. Set firstname to "1234567"
5. Observe the response

**Request Body:**
```json
{
  "firstname": "1234567",
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

400 Bad Request. Numeric strings should be rejected in name fields.

---

## Actual Result

200 OK. Booking is created with '1234567' as the firstname.

---

## Evidence

![Screenshot](screenshots/BUG-003-01-screenshot.jpeg)

---

## Impact

Invalid data types are accepted in name fields. In a production system, this would result in corrupted guest records and broken identity verification.
