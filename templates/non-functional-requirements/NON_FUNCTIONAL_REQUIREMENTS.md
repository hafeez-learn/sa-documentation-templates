# Non-Functional Requirements Template

## Project Name
[Project Name]

---

## 1. Performance Requirements

### 1.1 Response Time
| Metric | Target | Measurement Point |
|--------|--------|-------------------|
| Page Load Time | < 3 seconds | Network edge |
| API Response (p95) | < 500ms | Server endpoint |
| API Response (p99) | < 1000ms | Server endpoint |
| Batch Processing | < 30 seconds | Per 1000 records |

### 1.2 Throughput
| Operation | Expected Volume | Peak Volume |
|-----------|----------------|-------------|
| [Operation 1] | [X] TPS | [Y] TPS |
| [Operation 2] | [X] TPS | [Y] TPS |

### 1.3 Capacity
- **Concurrent Users:** [Number]
- **Data Storage:** [Size] over [Time period]
- **API Rate Limits:** [Number] requests per [Time unit]

---

## 2. Availability Requirements

### 2.1 Uptime Targets
| System Tier | Availability | Downtime Allowed/Month |
|-------------|--------------|------------------------|
| Critical Systems | 99.99% | 4.4 minutes |
| Standard Systems | 99.9% | 43.8 minutes |
| Batch/Background | 99.0% | 7.3 hours |

### 2.2 Maintenance Windows
- **Planned Maintenance:** [Day/Time], [Duration]
- **Notification Required:** [Advance notice period]

### 2.3 Recovery Requirements
- **RTO (Recovery Time Objective):** [Duration]
- **RPO (Recovery Point Objective):** [Duration]

---

## 3. Security Requirements

### 3.1 Authentication & Authorization
| Requirement | Standard/Framework |
|-------------|-------------------|
| Password Policy | [e.g., NIST guidelines] |
| Session Timeout | [Duration] |
| MFA Required For | [User types/systems] |
| API Authentication | [Method] |

### 3.2 Data Protection
| Data Classification | Protection Required |
|--------------------|--------------------|
| Public | [Protection level] |
| Internal | [Protection level] |
| Confidential | [Protection level] |
| Restricted | [Protection level] |

### 3.3 Compliance
- [ ] GDPR Compliance Required
- [ ] PCI-DSS Compliance Required
- [ ] SOC 2 Compliance Required
- [ ] ISO 27001 Compliance Required

### 3.4 Audit Logging
- Log all authentication attempts
- Log all data access to confidential/restricted data
- Log all administrative actions
- Log retention period: [Duration]

---

## 4. Scalability Requirements

### 4.1 Horizontal Scaling
- System must support adding nodes without downtime
- State management must be distributed (no single point of failure)
- Database must support read replicas

### 4.2 Vertical Scaling
- Maximum supported configuration per node: [Specs]
- Scaling trigger: [CPU/Memory threshold]

### 4.3 Auto-Scaling Triggers
| Metric | Scale Up Threshold | Scale Down Threshold |
|--------|-------------------|---------------------|
| CPU | > 80% | < 20% for 10 min |
| Memory | > 85% | < 30% for 10 min |
| Request Queue | > 100 | < 10 for 15 min |

---

## 5. Reliability Requirements

### 5.1 Error Handling
- All errors must be logged with correlation ID
- System must not crash on invalid input
- Graceful degradation required for non-critical failures

### 5.2 Retry Policies
| Operation Type | Retry Count | Backoff |
|---------------|-------------|---------|
| Network Calls | 3 | Exponential |
| Database Writes | 2 | Linear |
| External API | 5 | Exponential |

### 5.3 Circuit Breaker
- Trigger after [X] consecutive failures
- Half-open after [Duration]
- Reset after [X] successes in half-open state

---

## 6. Maintainability Requirements

### 6.1 Code Quality
- Minimum code coverage: [Percentage]
- All critical paths must have unit tests
- Code review required for all changes

### 6.2 Deployment
- Zero-downtime deployment required
- Blue-green or canary deployment strategy
- Rollback capability within [Duration]

### 6.3 Monitoring & Observability
- All services must expose metrics endpoint
- Distributed tracing required
- Structured logging format (JSON)
- Log levels: ERROR, WARN, INFO, DEBUG

---

## 7. Usability Requirements

### 7.1 Accessibility
- WCAG 2.1 Level [A/AA/AAA] compliance
- Keyboard navigation support
- Screen reader compatibility

### 7.2 User Experience
- Maximum [X] clicks to complete any action
- Inline help for complex fields
- Clear error messages with resolution steps

### 7.3 Browser/Device Support
| Browser | Minimum Version |
|---------|----------------|
| Chrome | [Version] |
| Firefox | [Version] |
| Safari | [Version] |
| Edge | [Version] |

---

## 8. Data Requirements

### 8.1 Data Retention
| Data Category | Retention Period | Archive Policy |
|--------------|------------------|----------------|
| Transaction Data | [Period] | [Policy] |
| Audit Logs | [Period] | [Policy] |
| User Data | [Period] | [Policy] |

### 8.2 Data Migration
- Zero data loss during migration
- Rollback capability
- Parallel run period: [Duration]

---

## 9. Compliance & Governance

### 9.1 Regulatory Requirements
| Regulation | Applicability | Compliance Deadline |
|------------|---------------|---------------------|
| [Regulation 1] | [Yes/No] | [Date] |

### 9.2 Internal Policies
- Information Security Policy
- Data Classification Policy
- Change Management Policy

---

## 10. Business Continuity

### 10.1 Disaster Recovery
- DR site location: [Location]
- Data replication method: [Method]
- DR test frequency: [Frequency]

### 10.2 Backup Requirements
- Full backup frequency: [Frequency]
- Incremental backup frequency: [Frequency]
- Backup retention: [Duration]
- Backup encryption: [Yes/No]

---

*Document Control:*
- *Version:* [Version]
- *Author:* [Author]
- *Reviewed By:* [Reviewer]
- *Approved By:* [Approver]
