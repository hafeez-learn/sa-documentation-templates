# Use Cases Template

## Project: [Project Name]

---

## UC-001: [Use Case Name]

| Field | Value |
|-------|-------|
| **Use Case ID** | UC-001 |
| **Use Case Name** | [Name] |
| **Actor** | [Primary Actor] |
| **Secondary Actors** | [Other actors] |
| **Trigger** | [What initiates this use case] |
| **Pre-condition** | [What must be true before] |
| **Post-condition (Success)** | [What is true on success] |
| **Post-condition (Failure)** | [What is true on failure] |
| **Priority** | [High/Medium/Low] |

### Main Flow

| Step | Actor Action | System Response |
|------|-------------|------------------|
| 1 | [Actor does something] | [System responds] |
| 2 | [Actor does something] | [System responds] |
| 3 | [Actor does something] | [System validates and processes] |
| 4 | | [System displays result] |

### Alternative Flows

#### Alternative Flow 1: [Name]
| Step | Description |
|------|-------------|
| 1 | [When this condition occurs] |
| 2 | [Alternative action] |
| 3 | Return to step [X] in main flow |

#### Alternative Flow 2: [Name]
| Step | Description |
|------|-------------|
| 1 | [Condition] |
| 2 | [Action] |

### Exception Flows

#### Exception 1: [Name]
| Step | Description |
|------|-------------|
| 1 | [Error condition detected] |
| 2 | [Error message displayed] |
| 3 | [Return to step X / Abort] |

### Business Rules
- [Rule 1]
- [Rule 2]

### Data Requirements
| Data Entity | Fields Used | Access |
|-------------|-------------|--------|
| [Entity] | [Fields] | Read/Write |

### UI/UX Requirements
- [Screen/Mockup reference]
- [Field validations]

---

## UC-002: [Use Case Name]

| Field | Value |
|-------|-------|
| **Use Case ID** | UC-002 |
| **Use Case Name** | [Name] |
| **Actor** | [Primary Actor] |
| **Trigger** | [Trigger] |
| **Priority** | [Priority] |

### Main Flow

| Step | Actor Action | System Response |
|------|-------------|------------------|
| 1 | | |
| 2 | | |
| 3 | | |

[Repeat same structure as UC-001]

---

## Use Case Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│   ┌─────────┐                              ┌──────────┐    │
│   │  Actor  │                              │ System   │    │
│   │  (User) │                              │          │    │
│   └────┬────┘                              └────┬─────┘    │
│        │                                        │          │
│        │ ──── UC-001: [Action] ────────────────▶          │
│        │                                        │          │
│        │ ◀──── UC-002: [Response] ─────────────          │
│        │                                        │          │
│        │ ──── UC-003: [Action] ────────────────▶          │
│        │                                        │          │
│   ┌────┴────┐                              ┌────┴─────┐    │
│   │ Actor 2 │                              │   DB     │    │
│   └─────────┘                              └──────────┘    │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## Traceability Matrix

| Use Case | Functional Req | Acceptance Criteria | Test Case |
|----------|---------------|---------------------|-----------|
| UC-001 | FR-001, FR-002 | AC-001, AC-002 | TC-001 |
| UC-002 | FR-003 | AC-003 | TC-002 |
| UC-003 | FR-004, FR-005 | AC-004, AC-005 | TC-003 |

---

## Use Case Prioritization

| Priority | Use Cases | Rationale |
|----------|-----------|-----------|
| P0 (Must Have) | UC-001, UC-002 | Core business process |
| P1 (Should Have) | UC-003 | Important but deferrable |
| P2 (Nice to Have) | UC-004, UC-005 | Enhancement |

---

*Document Control:*
- *Created:* [Date]
- *Author:* [Name]
- *Status:* [Draft/Reviewed/Approved]
