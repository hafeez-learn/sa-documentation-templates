# Digital Banking API - Use Cases
## Case Study for System Analyst Role

---

## UC-001: Create Account

| Field | Value |
|-------|-------|
| **Use Case ID** | UC-001 |
| **Use Case Name** | Create New Account |
| **Actor** | Bank Operations Staff |
| **Secondary Actors** | System (validates uniqueness) |
| **Trigger** | Customer opens new bank account |
| **Pre-condition** | Customer has valid identity documents |
| **Post-condition (Success)** | New account created with ACTIVE status |
| **Post-condition (Failure)** | No account created; error returned |
| **Priority** | P0 (Critical) |

### Main Flow

| Step | Actor Action | System Response |
|------|-------------|------------------|
| 1 | Operations staff initiates account creation | System displays account form |
| 2 | Staff enters customer details (name, NRIC, initial deposit) | System validates input format |
| 3 | Staff submits form | System generates unique account number |
| 4 | | System validates NRIC uniqueness |
| 5 | | System creates account record |
| 6 | | System returns account confirmation |

### Alternative Flows

#### Alt-1: Duplicate NRIC
| Step | Description |
|------|-------------|
| 1 | When: NRIC already exists in system |
| 2 | System rejects with "Customer already exists" |
| 3 | Use case ends |

#### Alt-2: Duplicate Account Number
| Step | Description |
|------|-------------|
| 1 | When: Generated account number collides |
| 2 | System regenerates account number |
| 3 | Returns to step 3 of main flow |

### Exception Flows

#### Ex-1: Invalid NRIC Format
| Step | Description |
|------|-------------|
| 1 | System detects invalid NRIC format |
| 2 | System returns validation error with expected format |
| 3 | Use case ends |

### Business Rules
- BR-001: Account number must be unique (12 digits, format: ACC + 9 digits)
- BR-002: NRIC format: S/T/F/G + 7 digits + A-Z checksum
- BR-003: Initial deposit minimum: $0 (zero allowed for opening)
- BR-004: New accounts default to ACTIVE status

---

## UC-002: Check Account Balance

| Field | Value |
|-------|-------|
| **Use Case ID** | UC-002 |
| **Use Case Name** | Enquire Account Balance |
| **Actor** | Account Holder |
| **Trigger** | Customer requests balance information |
| **Pre-condition** | Customer is authenticated |
| **Post-condition (Success)** | Balance information displayed |
| **Post-condition (Failure)** | Error returned if account not found |
| **Priority** | P0 (Critical) |

### Main Flow

| Step | Actor Action | System Response |
|------|-------------|------------------|
| 1 | Customer enters account number | System validates account exists |
| 2 | Customer requests balance | |
| 3 | | System retrieves account balance |
| 4 | | System returns balance and account status |

### Alternative Flows

#### Alt-1: Account Suspended
| Step | Description |
|------|-------------|
| 1 | Account status is SUSPENDED |
| 2 | System returns balance but with warning |
| 3 | Customer advised to contact bank |

### Exception Flows

#### Ex-1: Account Not Found
| Step | Description |
|------|-------------|
| 1 | Account number not in system |
| 2 | System returns 404 error |
| 3 | Use case ends |

---

## UC-003: Transfer Funds

| Field | Value |
|-------|-------|
| **Use Case ID** | UC-003 |
| **Use Case Name** | Initiate Fund Transfer |
| **Actor** | Account Holder |
| **Secondary Actors** | External Bank System (for interbank) |
| **Trigger** | Customer initiates transfer |
| **Pre-condition** | Customer authenticated, source account has sufficient funds |
| **Post-condition (Success)** | Funds transferred, transaction recorded |
| **Post-condition (Failure)** | Transaction rejected, no funds moved |
| **Priority** | P0 (Critical) |

### Main Flow

| Step | Actor Action | System Response |
|------|-------------|------------------|
| 1 | Customer enters source account | System validates account exists |
| 2 | Customer enters destination account | System validates format |
| 3 | Customer enters amount | System validates amount > 0 |
| 4 | Customer confirms transfer | System checks sufficient balance |
| 5 | | System debits source account |
| 6 | | System credits destination account |
| 7 | | System generates transaction reference |
| 8 | | System returns confirmation |

### Alternative Flows

#### Alt-1: Same Source and Destination
| Step | Description |
|------|-------------|
| 1 | Source equals destination account |
| 2 | System rejects with "Cannot transfer to same account" |
| 3 | Use case ends |

#### Alt-2: Insufficient Balance
| Step | Description |
|------|-------------|
| 1 | Balance < transfer amount |
| 2 | System rejects with "Insufficient funds" |
| 3 | Use case ends |

### Exception Flows

#### Ex-1: Destination Account Not Found
| Step | Description |
|------|-------------|
| 1 | Destination account invalid |
| 2 | System rejects transfer |
| 3 | Use case ends |

### Business Rules
- BR-010: Transfer amount must be positive
- BR-011: Source and destination cannot be same
- BR-012: Transaction reference format: TXN + 16 alphanumeric
- BR-013: Both accounts must be in ACTIVE status

---

## UC-004: Generate Payment QR Code

| Field | Value |
|-------|-------|
| **Use Case ID** | UC-004 |
| **Use Case Name** | Generate PayNow QR Code |
| **Actor** | Merchant |
| **Trigger** | Merchant initiates payment request |
| **Pre-condition** | Merchant account is ACTIVE |
| **Post-condition (Success)** | QR code generated with expiry |
| **Post-condition (Failure)** | Error returned |
| **Priority** | P1 (Important) |

### Main Flow

| Step | Actor Action | System Response |
|------|-------------|------------------|
| 1 | Merchant enters account number | System validates account |
| 2 | Merchant enters payment amount | System validates amount |
| 3 | Merchant enters reference | System validates reference |
| 4 | Merchant requests QR | System generates unique payment ID |
| 5 | | System encodes QR data |
| 6 | | System sets expiry (5 minutes) |
| 7 | | System returns QR code image |

### Alternative Flows

#### Alt-1: Amount Exceeds Limit
| Step | Description |
|------|-------------|
| 1 | Amount > $10,000 |
| 2 | System generates QR with warning flag |
| 3 | Continues to step 6 |

### Business Rules
- BR-020: QR code expires after 5 minutes
- BR-021: Maximum single payment: $50,000
- BR-022: QR contains: payment_id, account, amount, merchant_ref, expiry

---

## UC-005: Confirm Payment

| Field | Value |
|-------|-------|
| **Use Case ID** | UC-005 |
| **Use Case Name** | Confirm QR Payment |
| **Actor** | Paying Customer |
| **Trigger** | Customer scans merchant QR code |
| **Pre-condition** | QR code is valid and not expired |
| **Post-condition (Success)** | Payment executed, both parties notified |
| **Post-condition (Failure)** | Payment rejected, no funds moved |
| **Priority** | P0 (Critical) |

### Main Flow

| Step | Actor Action | System Response |
|------|-------------|------------------|
| 1 | Customer scans QR code | System decodes payment ID |
| 2 | Customer enters amount | System validates amount matches QR |
| 3 | Customer confirms payment | System checks sufficient balance |
| 4 | | System marks payment as PENDING |
| 5 | | System executes transfer |
| 6 | | System updates payment status to COMPLETED |
| 7 | | System sends notifications |
| 8 | | System returns confirmation |

### Exception Flows

#### Ex-1: Payment Expired
| Step | Description |
|------|-------------|
| 1 | Current time > QR expiry time |
| 2 | System rejects with "Payment expired" |
| 3 | Use case ends |

#### Ex-2: Duplicate Confirmation (Idempotency)
| Step | Description |
|------|-------------|
| 1 | Payment already COMPLETED |
| 2 | System returns original confirmation |
| 3 | No duplicate processing |

### Business Rules
- BR-030: Payment amount must match QR amount
- BR-031: Customer account must have sufficient funds
- BR-032: Payment can only be confirmed once (idempotent)
- BR-033: Merchant receives notification within 1 second

---

## Use Case Traceability Matrix

| Use Case | Functional Requirements | Test Cases |
|----------|------------------------|------------|
| UC-001 | FR-001 | TC-001, TC-002, TC-003 |
| UC-002 | FR-002 | TC-004, TC-005 |
| UC-003 | FR-003, FR-004 | TC-006, TC-007, TC-008, TC-009 |
| UC-004 | FR-005 | TC-010, TC-011 |
| UC-005 | FR-006 | TC-012, TC-013, TC-014 |

---

*Document Control:*
- *Version:* 1.0
- *Author:* Hafeez
- *Date:* 2026-04-16
