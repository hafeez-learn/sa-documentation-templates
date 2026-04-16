# User Stories Template

## Project: [Project Name]

---

## User Story Template

```
┌────────────────────────────────────────────────────────────┐
│ USER STORY #[Number]                                        │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  As a [WHO]                                                │
│  I want to [WHAT]                                          │
│  So that [WHY/BENEFIT]                                     │
│                                                            │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  Acceptance Criteria:                                      │
│  ┌──────────────────────────────────────────────────────┐  │
│  │ Given [CONTEXT]                                      │  │
│  │ When [ACTION]                                        │  │
│  │ Then [EXPECTED_RESULT]                               │  │
│  │                                                      │  │
│  │ Given [CONTEXT]                                      │  │
│  │ When [ACTION]                                        │  │
│  │ Then [EXPECTED_RESULT]                               │  │
│  └──────────────────────────────────────────────────────┘  │
│                                                            │
│  Story Points: [Number]  │  Priority: [H/M/L]              │
│  Sprint: [Sprint Name]   │  Status: [To Do/In Progress]   │
│                                                            │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  Technical Notes:                                           │
│  - [Technical consideration 1]                              │
│  - [Technical consideration 2]                              │
│                                                            │
│  Dependencies:                                             │
│  - [Depends on US-XXX]                                    │
│  - [Blocked by: Task-XXX]                                  │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

---

## EPIC: [Epic Name]

**Description:** [What this epic encompasses]

---

### USER STORY 001: [Story Title]

```
As a [Bank Customer]
I want to view my account balance
So that I can know how much money I have available
```

**Acceptance Criteria:**

| # | Given | When | Then |
|---|-------|------|------|
| 1 | I am logged into my account | I navigate to account summary | My current balance is displayed |
| 2 | I have multiple accounts | I view my accounts | Each account balance is shown |
| 3 | My balance was updated | I refresh the page | The latest balance is shown |

**Story Points:** 3  
**Priority:** High  
**Sprint:** Sprint 1

---

### USER STORY 002: [Story Title]

```
As a [Bank Customer]
I want to transfer money to another account
So that I can pay bills and send money to family
```

**Acceptance Criteria:**

| # | Given | When | Then |
|---|-------|------|------|
| 1 | I have sufficient balance | I enter transfer details | Transfer is processed |
| 2 | I enter invalid account | I submit transfer | Error message is shown |
| 3 | Transfer exceeds limit | I submit transfer | Transfer is rejected with reason |

**Story Points:** 5  
**Priority:** High  
**Sprint:** Sprint 1

---

## Template Format (for new stories)

### USER STORY XXX: [Title]

```
As a [ROLE]
I want to [FEATURE]
So that [VALUE]
```

**Acceptance Criteria:**
```
Given [context]
When [action]
Then [result]

Given [context]
When [action]
Then [result]
```

**Notes:**
- Story Points: __
- Priority: [H/M/L]
- Sprint: ___

---

## User Story Mapping

### Release 1.0

```
┌─────────────────────────────────────────────────────────────┐
│ BACKLOG                                                     │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐         │
│  │  Sprint 1   │  │  Sprint 2   │  │  Sprint 3   │         │
│  ├─────────────┤  ├─────────────┤  ├─────────────┤         │
│  │ US-001 (3) │  │ US-004 (3) │  │ US-007 (5) │         │
│  │ US-002 (5) │  │ US-005 (5) │  │ US-008 (3) │         │
│  │ US-003 (3) │  │ US-006 (3) │  │ US-009 (5) │         │
│  └─────────────┘  └─────────────┘  └─────────────┘         │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Capacity Planning

| Sprint | User Stories | Total Points | Velocity |
|--------|--------------|---------------|----------|
| Sprint 1 | US-001, US-002, US-003 | 11 | - |
| Sprint 2 | US-004, US-005, US-006 | 11 | - |
| Sprint 3 | US-007, US-008, US-009 | 13 | - |

---

## Definition of Ready (DoR)

Before a user story can be committed to a sprint:

- [ ] User story is written in standard format
- [ ] Acceptance criteria are defined
- [ ] Acceptance criteria are testable
- [ ] Dependencies are identified
- [ ] Effort (story points) is estimated
- [ ] Priority is assigned
- [ ] Acceptance criteria reviewed by QA

---

## Definition of Done (DoD)

For a user story to be considered complete:

- [ ] Code is written and reviewed
- [ ] Unit tests written and passing
- [ ] Integration tests passing
- [ ] Acceptance criteria met
- [ ] Documentation updated
- [ ] Deployed to staging environment
- [ ] Product Owner acceptance obtained

---

## INVEST Checklist

| Criterion | Description | Met? |
|-----------|-------------|------|
| **I**ndependent | Can be developed independently | [ ] |
| **N**egotiable | Not overly specified, open to discussion | [ ] |
| **V**aluable | Delivers value to the user | [ ] |
| **E**stimable | Can be reasonably estimated | [ ] |
| **S**mall | Can be completed in one sprint | [ ] |
| **T**estable | Can be verified as complete | [ ] |

---

*Document Control:*
- *Version:* 1.0
- *Author:* [Name]
- *Sprint Master:* [Name]
