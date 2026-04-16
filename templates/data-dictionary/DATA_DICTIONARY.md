# Data Dictionary Template

## Project: [Project Name]

---

## Data Dictionary Overview

| Entity Name | Description | Owner | Classification |
|-------------|-------------|-------|-----------------|
| [Entity] | [Description] | [Owner] | [Classification] |

---

## Entity: [Entity Name]

### Basic Information
| Field | Value |
|-------|-------|
| **Table Name** | [table_name] |
| **Description** | [Description of what this table stores] |
| **Owner** | [Data Owner] |
| **Classification** | [Confidential/Internal/Public] |
| **Retention Period** | [Duration] |

### Schema Definition

```
┌────────────────────────────────────────────────────────────┐
│ TABLE: [table_name]                                        │
├────────────────────────────────────────────────────────────┤
│ Column Name      │ Data Type    │ Constraints │ Description│
│ ─────────────────────────────────────────────────────────  │
│ [column_1]       │ [TYPE]       │ [PK, NN]   │ [Desc]    │
│ [column_2]       │ [TYPE]       │ [FK, NN]   │ [Desc]    │
│ [column_3]       │ [TYPE]       │ [UQ]       │ [Desc]    │
│ [column_4]       │ [TYPE]       │ [CK]       │ [Desc]    │
│ [created_at]     │ TIMESTAMP    │ [NN, Dflt] │ [Desc]    │
│ [updated_at]     │ TIMESTAMP    │ [NN, Dflt] │ [Desc]    │
└────────────────────────────────────────────────────────────┘

NN = NOT NULL | PK = PRIMARY KEY | FK = FOREIGN KEY
UQ = UNIQUE | CK = CHECK CONSTRAINT | Dflt = DEFAULT
```

### Column Details

#### [column_1]
| Property | Value |
|----------|-------|
| **Data Type** | [VARCHAR(50)/INTEGER/DECIMAL/etc.] |
| **Nullable** | [Yes/No] |
| **Default** | [Value or N/A] |
| **Description** | [Description] |
| **Sample Values** | [Value1], [Value2], [Value3] |
| **Business Rules** | [Rule1], [Rule2] |

#### [column_2]
| Property | Value |
|----------|-------|
| **Data Type** | [TYPE] |
| **References** | [foreign_table(foreign_column)] |
| **On Delete** | [CASCADE/SET NULL/RESTRICT] |
| **On Update** | [CASCADE/SET NULL/RESTRICT] |

### Indexes

| Index Name | Columns | Type | Unique | Purpose |
|------------|---------|------|--------|---------|
| idx_[name] | [col1, col2] | B-Tree | Yes/No | [Performance/Unique] |

### Relationships

| Relationship | Cardinality | From | To |
|--------------|-------------|------|-----|
| [Relation 1] | [1:N / N:1 / N:N] | [table.col] | [table.col] |

### Data Sample

| column_1 | column_2 | column_3 |
|----------|----------|----------|
| [Value] | [Value] | [Value] |
| [Value] | [Value] | [Value] |

---

## Entity: [Account]

### Basic Information
| Field | Value |
|-------|-------|
| **Table Name** | accounts |
| **Description** | Stores customer account information |
| **Owner** | Banking Operations |
| **Classification** | Confidential |

### Schema Definition

```
┌────────────────────────────────────────────────────────────┐
│ TABLE: accounts                                            │
├────────────────────────────────────────────────────────────┤
│ Column Name      │ Data Type       │ Constraints    │ Desc│
│ ─────────────────────────────────────────────────────────  │
│ id               │ BIGINT          │ PK, NN, AI     │ PK  │
│ account_number   │ VARCHAR(20)     │ NN, UQ         │ Acct│
│ holder_name      │ VARCHAR(100)    │ NN             │ Name│
│ nric             │ VARCHAR(20)     │ NN             │ NRIC│
│ balance          │ DECIMAL(15,2)  │ NN, DFLT(0)   │ Bal │
│ status           │ VARCHAR(20)     │ NN, DFLT      │ Stat│
│ created_at       │ TIMESTAMP       │ NN, DFLT(NOW) │ Crtd│
│ updated_at       │ TIMESTAMP       │ NN, DFLT(NOW) │ Updt│
└────────────────────────────────────────────────────────────┘
```

### Field Descriptions

| Column | Description | Valid Values | Business Rules |
|--------|-------------|--------------|----------------|
| id | Auto-generated primary key | Positive integers | System-assigned |
| account_number | Unique account identifier | 12 digits | Must be unique, format: ACC + 9 digits |
| holder_name | Full name of account holder | Any name | Minimum 2 characters |
| nric | National ID number | 9 characters | Format: S/T/F/G + 7 digits + A-Z |
| balance | Current account balance | Decimal | Cannot be negative |
| status | Account status | ACTIVE, INACTIVE, SUSPENDED, CLOSED | Default: ACTIVE |
| created_at | Record creation timestamp | Timestamp | Auto-set on insert |
| updated_at | Record update timestamp | Timestamp | Auto-set on update |

### Indexes

| Index | Columns | Type | Purpose |
|-------|---------|------|---------|
| idx_account_number | account_number | B-Tree | Fast lookup by account |
| idx_status | status | B-Tree | Filter by status |

---

## Data Governance

### Data Ownership

| Data Domain | Data Owner | Data Steward |
|-------------|------------|--------------|
| Customer Data | [Name] | [Name] |
| Account Data | [Name] | [Name] |
| Transaction Data | [Name] | [Name] |

### Data Quality Rules

| Rule | Description | Validation Frequency |
|------|-------------|---------------------|
| DQ-001 | No duplicate account numbers | On insert |
| DQ-002 | Balance must be non-negative | On update |
| DQ-003 | Valid status values only | On update |

### Sensitive Data Handling

| Data Element | Classification | Masking Required | Encryption |
|--------------|----------------|-------------------|------------|
| NRIC | Restricted | Yes (last 4 chars visible) | At rest |
| Account Balance | Confidential | No | At rest |

---

## Database Version

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | [Date] | [Name] | Initial schema |

---

*Document Control:*
- *Version:* 1.0
- *Author:* [Name]
- *Data Owner:* [Name]
- *Last Updated:* [Date]
