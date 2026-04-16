# Digital Banking API - User Stories
## Case Study for System Analyst Role

---

## EPIC: Digital Banking Platform

**Description:** Enable customers to perform banking operations (account management, transfers, payments) through a secure API platform.

---

### US-001: Account Creation

```
As a Bank Operations Team
I want to create new customer accounts
So that customers can access banking services
```

**Acceptance Criteria:**

| # | Given | When | Then |
|---|-------|------|------|
| 1 | I am authorized as admin | I submit valid account details | Account is created with ACTIVE status |
| 2 | I submit duplicate account number | I submit the request | System returns 400 with error message |
| 3 | I submit invalid NRIC format | I submit the request | System returns 400 with validation error |
| 4 | I submit negative initial balance | I submit the request | System returns 400 with validation error |

**Story Points:** 3  
**Priority:** P0 (Must Have)  
**Sprint:** Sprint 1

---

### US-002: Balance Enquiry

```
As a Bank Customer
I want to check my account balance
So that I know my available funds
```

**Acceptance Criteria:**

| # | Given | When | Then |
|---|-------|------|------|
| 1 | Account ACC001 exists with balance $1000 | I query balance | Balance $1000 is returned |
| 2 | Account does not exist | I query balance | 404 error returned |
| 3 | Account is SUSPENDED | I query balance | Account status shown but transactions blocked |

**Story Points:** 2  
**Priority:** P0 (Must Have)  
**Sprint:** Sprint 1

---

### US-003: Fund Transfer

```
As a Bank Customer
I want to transfer money to another account
So that I can pay bills and send money
```

**Acceptance Criteria:**

| # | Given | When | Then |
|---|-------|------|------|
| 1 | Sufficient balance in source account | I submit valid transfer | Transfer completes, both balances updated |
| 2 | Insufficient balance | I submit transfer | Transfer rejected with "Insufficient funds" |
| 3 | Same source and destination account | I submit transfer | Transfer rejected with error |
| 4 | Transfer amount is zero or negative | I submit transfer | Validation error returned |

**Story Points:** 5  
**Priority:** P0 (Must Have)  
**Sprint:** Sprint 2

---

### US-004: QR Code Payment Generation

```
As a Merchant
I want to generate a payment QR code
So that customers can scan and pay me
```

**Acceptance Criteria:**

| # | Given | When | Then |
|---|-------|------|------|
| 1 | Valid account and amount | I generate QR | Valid QR code is returned |
| 2 | Amount exceeds limit ($10,000) | I generate QR | QR generated with warning flag |
| 3 | Account is CLOSED | I generate QR | Error returned, QR not generated |

**Story Points:** 3  
**Priority:** P1 (Should Have)  
**Sprint:** Sprint 2

---

### US-005: Payment Confirmation

```
As a Bank Customer
I want to confirm a QR payment
So that I can complete a purchase
```

**Acceptance Criteria:**

| # | Given | When | Then |
|---|-------|------|------|
| 1 | Valid payment reference | I confirm payment | Payment marked as COMPLETED |
| 2 | Payment already confirmed | I try to confirm again | Error returned (idempotency) |
| 3 | Payment expired (>5 minutes) | I confirm | Error returned "Payment expired" |

**Story Points:** 5  
**Priority:** P0 (Must Have)  
**Sprint:** Sprint 2

---

### US-006: Transaction History

```
As a Bank Customer
I want to view my transaction history
So that I can track my spending
```

**Acceptance Criteria:**

| # | Given | When | Then |
|---|-------|------|------|
| 1 | I have 10 transactions | I query history | All 10 transactions returned, newest first |
| 2 | No transactions exist | I query history | Empty list returned |
| 3 | I filter by date range | I query with dates | Only transactions within range returned |

**Story Points:** 3  
**Priority:** P1 (Should Have)  
**Sprint:** Sprint 3

---

## Sprint Mapping

| Sprint | User Stories | Total Points |
|--------|--------------|--------------|
| Sprint 1 | US-001, US-002 | 5 |
| Sprint 2 | US-003, US-004, US-005 | 13 |
| Sprint 3 | US-006 | 3 |
| **Total** | | **21** |

---

## Definition of Ready

- [x] User story written in standard format
- [x] Acceptance criteria defined
- [x] Acceptance criteria are testable
- [x] Dependencies identified (US-001 before US-002)
- [x] Effort estimated (story points assigned)
- [x] Priority assigned
- [x] Acceptance criteria reviewed by QA

---

## Definition of Done

- [x] Code written and reviewed
- [x] Unit tests written and passing
- [x] Integration tests passing
- [x] All acceptance criteria met
- [x] API documentation updated
- [x] Deployed to staging
- [x] Product Owner acceptance obtained

---

*Document Control:*
- *Version:* 1.0
- *Author:* Hafeez
- *Date:* 2026-04-16
