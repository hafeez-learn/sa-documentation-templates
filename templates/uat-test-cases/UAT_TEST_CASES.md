# UAT Test Cases Template

## Project: [Project Name]
## Test Suite: [Module/Sprint Name]

---

## Test Case Template

```
┌────────────────────────────────────────────────────────────┐
│ TEST CASE TC-XXX                                           │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  Test Case Name: [Descriptive Name]                        │
│  Test Type: [Positive/Negative/Edge Case/Boundary]        │
│  Module: [Module Name]                                     │
│  Related Requirements: [FR-XXX]                             │
│  Related Use Cases: [UC-XXX]                               │
│                                                            │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  PRE-CONDITIONS:                                           │
│  1. [Condition 1]                                          │
│  2. [Condition 2]                                          │
│                                                            │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  TEST DATA:                                                │
│  Field: [Value]                                            │
│  Field: [Value]                                            │
│                                                            │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  TEST STEPS:                                               │
│  ┌────┬────────────────────────────────────────────────┐   │
│  │ #  │ Step                                         │   │
│  ├────┼────────────────────────────────────────────────┤   │
│  │ 1  │ [Action to perform]                          │   │
│  │ 2  │ [Verify result]                             │   │
│  │ 3  │ [Next action]                               │   │
│  └────┴────────────────────────────────────────────────┘   │
│                                                            │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  EXPECTED RESULTS:                                         │
│  1. [Expected outcome 1]                                  │
│  2. [Expected outcome 2]                                  │
│                                                            │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  ACTUAL RESULTS:                                           │
│  1. [To be filled during testing]                          │
│  2. [To be filled during testing]                         │
│                                                            │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  TEST EXECUTED BY: ____________  DATE: ____________       │
│  TEST RESULT: [PASS / FAIL / BLOCKED / SKIPPED]           │
│  DEFECT ID (if failed): ____________                      │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

---

## Test Case Examples

### POSITIVE TEST CASES

#### TC-001: Successful Account Creation

| Field | Value |
|-------|-------|
| **Test Case Name** | Create New Account - Valid Data |
| **Test Type** | Positive |
| **Module** | Account Management |
| **Related Requirements** | FR-001 |

**Pre-conditions:**
1. User is logged in with admin privileges
2. System is operational

**Test Data:**
| Field | Value |
|-------|-------|
| Account Number | ACC-999-001 |
| Holder Name | John Doe |
| NRIC | S123456789A |
| Initial Balance | 1000.00 |

**Test Steps:**
| # | Action | Expected Result |
|---|--------|-----------------|
| 1 | Navigate to Account Management | Account screen displayed |
| 2 | Click "Create New Account" | Form displayed |
| 3 | Fill in valid account details | Fields accept input |
| 4 | Click "Submit" | Account created successfully |
| 5 | Verify confirmation message | "Account created successfully" shown |
| 6 | Verify account appears in list | Account visible in account list |

**Test Result:** PASS / FAIL

---

#### TC-002: Successful Balance Enquiry

| Field | Value |
|-------|-------|
| **Test Case Name** | Check Account Balance |
| **Test Type** | Positive |
| **Module** | Account Enquiry |
| **Related Requirements** | FR-002 |

**Test Data:**
| Field | Value |
|-------|-------|
| Account Number | ACC-001 |
| Expected Balance | 1000.00 |

**Test Steps:**
| # | Action | Expected Result |
|---|--------|-----------------|
| 1 | Enter account number | Field accepts input |
| 2 | Click "Check Balance" | System processes request |
| 3 | Verify balance displayed | Balance matches expected |

**Test Result:** PASS / FAIL

---

### NEGATIVE TEST CASES

#### TC-003: Account Creation with Duplicate Account Number

| Field | Value |
|-------|-------|
| **Test Case Name** | Create Account - Duplicate Account Number |
| **Test Type** | Negative |
| **Module** | Account Management |
| **Related Requirements** | FR-001 |

**Pre-conditions:**
- Account number ACC-001 already exists in system

**Test Steps:**
| # | Action | Expected Result |
|---|--------|-----------------|
| 1 | Navigate to create account | Form displayed |
| 2 | Enter existing account number ACC-001 | Input accepted |
| 3 | Fill other required fields | Fields accept input |
| 4 | Click "Submit" | Validation error displayed |
| 5 | Verify error message | "Account number already exists" shown |

**Test Result:** PASS / FAIL

---

#### TC-004: Transfer with Insufficient Balance

| Field | Value |
|-------|-------|
| **Test Case Name** | Transfer - Insufficient Funds |
| **Test Type** | Negative |
| **Module** | Fund Transfer |
| **Related Requirements** | FR-005 |

**Test Data:**
| Field | Value |
|-------|-------|
| From Account | ACC-001 (Balance: $100) |
| To Account | ACC-002 |
| Transfer Amount | $500 |

**Test Steps:**
| # | Action | Expected Result |
|---|--------|-----------------|
| 1 | Select source account ACC-001 | Account selected |
| 2 | Enter transfer amount $500 | Amount entered |
| 3 | Select destination account ACC-002 | Account selected |
| 4 | Click "Transfer" | Transfer rejected |
| 5 | Verify error message | "Insufficient balance" shown |

**Test Result:** PASS / FAIL

---

### BOUNDARY/EDGE TEST CASES

#### TC-005: Transfer at Exact Balance Limit

| Field | Value |
|-------|-------|
| **Test Case Name** | Transfer - Exact Balance Amount |
| **Test Type** | Boundary |
| **Module** | Fund Transfer |

**Test Data:**
| Field | Value |
|-------|-------|
| From Account | ACC-001 (Balance: $100) |
| To Account | ACC-002 |
| Transfer Amount | $100 |

**Test Steps:**
| # | Action | Expected Result |
|---|--------|-----------------|
| 1 | Enter transfer amount equal to balance | $100 entered |
| 2 | Submit transfer | Transfer processed |
| 3 | Verify source account balance | Balance is $0 |
| 4 | Verify destination account credited | Balance increased by $100 |

**Test Result:** PASS / FAIL

---

## Test Summary Report

### Test Execution Summary

| Metric | Count |
|--------|-------|
| Total Test Cases | [X] |
| Passed | [X] |
| Failed | [X] |
| Blocked | [X] |
| Skipped | [X] |
| Pass Rate | [X]% |

### Defect Summary

| Defect ID | Description | Severity | Status |
|-----------|-------------|----------|--------|
| DEF-001 | [Description] | [High/Med/Low] | [Open/Fixed/Verified] |

### Risk Assessment

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| [Risk 1] | [H/M/L] | [H/M/L] | [Mitigation] |

---

## Sign-Off

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Business Analyst | | | |
| Product Owner | | | |
| QA Lead | | | |
| UAT Sponsor | | | |

---

*Document Control:*
- *Version:* 1.0
- *Author:* [Name]
- *Test Lead:* [Name]
