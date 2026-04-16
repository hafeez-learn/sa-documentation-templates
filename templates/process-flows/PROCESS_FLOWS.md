# Process Flows Template

## Project: [Project Name]

---

## Process Flow: [Process Name]

### Overview
| Field | Value |
|-------|-------|
| **Process ID** | PF-001 |
| **Process Name** | [Name] |
| **Owner** | [Name/Role] |
| **Trigger** | [What starts this process] |
| **End State** | [Final outcome] |

### Swimlane Diagram

```
┌──────────────┐ ┌──────────────┐ ┌──────────────┐ ┌──────────────┐
│   Actor 1    │ │   Actor 2    │ │    System    │ │   Actor 3    │
│              │ │              │ │              │ │              │
│              │ │              │ │              │ │              │
│    START     │ │              │ │              │ │              │
│      ◯       │ │              │ │              │ │              │
│      │       │ │              │ │              │ │              │
│      ▼       │ │              │ │              │ │              │
│ ┌─────────┐  │ │              │ │              │ │              │
│ │  Task   │  │ │              │ │              │ │              │
│ └────┬────┘  │ │              │ │              │ │              │
│      │       │ │              │ │              │ │              │
│      ▼       │ │              │ │              │ │              │
│              │ │ ┌─────────┐  │ │              │ │              │
│              │◀│ │ Validate │  │ │              │ │              │
│              │ │ └────┬────┘  │ │              │ │              │
│              │ │      │       │ │              │ │              │
│              │ │      ▼       │ │              │ │              │
│              │ │              │ │ ┌─────────┐  │ │              │
│              │ │              │◀│ │ Process │  │ │              │
│              │ │              │ │ └────┬────┘  │ │              │
│              │ │              │ │      │       │ │              │
│              │ │              │ │      ▼       │ │              │
│              │ │              │ │ ┌─────────┐  │ │              │
│              │ │              │ │ │  Notify │  │ │              │
│              │ │              │ │ └────┬────┘  │ │              │
│              │ │              │ │      │       │ │              │
│              ▼ │              ▼ │      ▼       ▼ │              │
│           END  │              │ │            END  │              │
│             ◯  │              │ │              ◯  │              │
└──────────────┘ └──────────────┘ └──────────────┘ └──────────────┘
```

### Process Steps

| Step | Actor | Action | System Response | Decision Point |
|------|-------|--------|-----------------|----------------|
| 1 | Customer | Initiates request | | |
| 2 | System | | Displays form | |
| 3 | Customer | Submits form | | Validate? |
| 4 | | | | YES → Continue |
| 5 | | | | NO → Show errors |
| 6 | Clerk | Reviews request | | Approve? |
| 7 | | | | YES → Process |
| 8 | | | | NO → Reject |

### Decision Table

| Condition | Action |
|-----------|--------|
| [Condition A] AND [Condition B] | [Action 1] |
| [Condition A] AND NOT [Condition B] | [Action 2] |
| NOT [Condition A] | [Action 3] |

### Business Rules Applied
1. [Rule 1]
2. [Rule 2]

### Exceptions

| Exception | Handling |
|-----------|----------|
| System unavailable | Queue request for retry |
| Invalid data | Return with error message |
| Timeout | Auto-logout, preserve draft |

### SLA

| Milestone | Target Time | Max Time |
|-----------|-------------|----------|
| Form submission | - | 5 min |
| Validation | 1 min | 2 min |
| Processing | 2 min | 5 min |
| Notification | 30 sec | 1 min |

---

## Flowchart Symbols

```
┌─────────────────────────────────────────────────────────────────┐
│ SYMBOL    │ NAME         │ USE                                 │
├───────────┼──────────────┼─────────────────────────────────────┤
│    ◯      │ Terminal     │ Start / End                         │
├───────────┼──────────────┼─────────────────────────────────────┤
│    ◇      │ Decision     │ Yes/No, True/False                  │
├───────────┼──────────────┼─────────────────────────────────────┤
│    ▭      │ Process      │ Action/Task                         │
├───────────┼──────────────┼─────────────────────────────────────┤
│    ⎍      │ Document     │ Output/Report                       │
├───────────┼──────────────┼─────────────────────────────────────┤
│    ⎙      │ Database     │ Data storage                        │
├───────────┼──────────────┼─────────────────────────────────────┤
│    ▼      │ Connector    │ Continue flow                       │
└─────────────────────────────────────────────────────────────────┘
```

---

*Document Control:*
- *Version:* 1.0
- *Author:* [Name]
- *Business Owner:* [Name]
