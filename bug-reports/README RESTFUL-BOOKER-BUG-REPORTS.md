# Restful-Booker API Bug Reports

**Application:** [Restful-Booker API](https://restful-booker.herokuapp.com)
**Tester:** Felicia Agbooluchi
**Testing Period:** June 2026
**Tool:** Postman
**Total Bugs Found:** 17

---

## Bug Index

| Bug ID | Title | Endpoint | Severity | Reproducibility |
|---|---|---|---|---|
| [BUG-001-01](./BUG-001-01-missing-firstname-500-error.md) | Missing firstname field returns 500 error | POST /booking | High | Intermittent |
| [BUG-001-02](./BUG-001-02-missing-lastname-500-error.md) | Missing lastname field returns 500 error | POST /booking | High | Intermittent |
| [BUG-001-03](./BUG-001-03-missing-totalprice-500-error.md) | Missing totalprice field returns 500 error | POST /booking | High | Intermittent |
| [BUG-001-04](./BUG-001-04-missing-depositpaid-500-error.md) | Missing depositpaid field returns 500 error | POST /booking | High | Intermittent |
| [BUG-001-05](./BUG-001-05-missing-checkin-500-error.md) | Missing checkin field returns 500 error | POST /booking | High | Intermittent |
| [BUG-001-06](./BUG-001-06-missing-checkout-500-error.md) | Missing checkout field returns 500 error | POST /booking | High | Intermittent |
| [BUG-002-01](./BUG-002-01-empty-firstname-accepted.md) | Empty firstname accepted and booking created | POST /booking | High | Always |
| [BUG-002-02](./BUG-002-02-empty-lastname-accepted.md) | Empty lastname accepted and booking created | POST /booking | High | Always |
| [BUG-002-03](./BUG-002-03-empty-checkin-accepted.md) | Empty checkin accepted and booking created | POST /booking | High | Always |
| [BUG-002-04](./BUG-002-04-empty-checkout-accepted.md) | Empty checkout accepted and booking created | POST /booking | High | Always |
| [BUG-003-01](./BUG-003-01-numeric-string-accepted-as-firstname.md) | Numeric string accepted as firstname | POST /booking | High | Always |
| [BUG-003-02](./BUG-003-02-special-chars-accepted-as-lastname.md) | Special characters accepted as lastname | POST /booking | High | Always |
| [BUG-003-03](./BUG-003-03-invalid-date-accepted-as-checkin.md) | Invalid date string accepted as checkin | POST /booking | High | Always |
| [BUG-003-04](./BUG-003-04-invalid-date-accepted-as-checkout.md) | Invalid date string accepted as checkout | POST /booking | High | Always |
| [BUG-004-01](./BUG-004-01-put-nonexistent-id-returns-405.md) | PUT non-existent ID returns 405 instead of 404 | PUT /booking/{id} | Medium | Always |
| [BUG-005-01](./BUG-005-01-patch-nonexistent-id-returns-403.md) | PATCH non-existent ID returns 403 instead of 404 | PATCH /booking/{id} | Medium | Always |
| [BUG-006-01](./BUG-006-01-delete-nonexistent-id-returns-405.md) | DELETE non-existent ID returns 405 instead of 404 | DELETE /booking/{id} | Medium | Always |

---

## Severity Breakdown

| Severity | Count |
|---|---|
| High | 14 |
| Medium | 3 |
| **Total** | **17** |
