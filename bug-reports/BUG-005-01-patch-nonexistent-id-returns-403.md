# BUG-005-01: PATCH /booking with Non-Existent ID Returns 403 Instead of 404

**Bug ID:** BUG-005-01
**Endpoint:** PATCH /booking/{id}
**Severity:** Medium
**Priority:** Medium
**Status:** Open
**Reproducibility:** Always
**Reported By:** Felicia Agbooluchi
**Date:** June 2026

---

## Summary

When a PATCH request is sent to update a booking using a non-existent ID with a valid token, the API returns 403 Forbidden instead of 404 Not Found.

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

API is accessible. Valid auth token generated via POST /auth.

---

## Steps to Reproduce

1. Generate a valid token via POST /auth with username: admin and password: password123
2. Send a PATCH request to https://restful-booker.herokuapp.com/booking/2130000000
3. Include valid token in the Cookie header as token={token}
4. Include a partial request body with firstname and lastname
5. Observe the response

**Request Body:**
```json
{
  "firstname": "Felicia",
  "lastname": "Agbo"
}
```

---

## Expected Result

404 Not Found. The API should confirm the booking ID does not exist.

---

## Actual Result

403 Forbidden. The API returns an authorization error instead of a not found error.

---

## Evidence

![Screenshot](screenshots/BUG-005-01-screenshot.jpeg)

---

## Impact

A 403 response misleads the client into thinking they lack permission rather than that the resource does not exist. This causes incorrect error handling on the client side.
