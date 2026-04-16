# System Analyst Documentation Templates

A collection of templates and a banking case study for System Analysts. Based on a Digital Banking API project.

## 📋 Templates Included

| Template | Purpose |
|----------|---------|
| **Functional Requirements** | Detailed FRD with acceptance criteria |
| **Non-Functional Requirements** | Performance, security, scalability, availability |
| **Use Cases** | Actor interactions, flows, decision tables |
| **User Stories** | Agile format with INVEST checklist |
| **UAT Test Cases** | Positive, negative, boundary testing |
| **Data Dictionary** | Entity definitions, field specs, relationships |
| **Process Flows** | Swimlane diagrams, decision trees |
| **Stakeholder Register** | RACI, communication plan |

## 🏦 Case Study: Digital Banking API

Real examples using a microservices banking platform:

- **Use Cases:** Account creation, balance enquiry, fund transfers, QR payments
- **User Stories:** Complete sprint backlog with acceptance criteria
- **Covers:** REST APIs, event-driven architecture, distributed transactions

## 📁 Project Structure

```
sa-documentation-templates/
├── templates/
│   ├── functional-requirements/
│   ├── non-functional-requirements/
│   ├── use-cases/
│   ├── user-stories/
│   ├── uat-test-cases/
│   ├── data-dictionary/
│   ├── process-flows/
│   └── stakeholder-register/
├── case-study/
│   └── banking-api/
│       ├── USE_CASES_BANKING.md
│       └── USER_STORIES_BANKING.md
└── README.md
```

## 🎯 How to Use These Templates

### 1. Functional Requirements
Copy `templates/functional-requirements/FUNCTIONAL_REQUIREMENTS.md` to your project and customize:
- Add your specific requirements
- Define clear acceptance criteria
- Map to use cases and test cases

### 2. Use Cases
Copy `templates/use-cases/USE_CASES.md` and fill in:
- Actor descriptions
- Main flow with steps
- Alternative and exception flows
- Business rules

### 3. User Stories
Use `templates/user-stories/USER_STORIES.md` format:
- Standard INVEST format
- Clear acceptance criteria (Given/When/Then)
- Story point estimation
- Sprint assignment

### 4. UAT Test Cases
Copy `templates/uat-test-cases/UAT_TEST_CASES.md`:
- Define pre-conditions
- List test data
- Document expected vs actual results
- Include sign-off section

## 📊 Deliverables Map

| SDLC Phase | Deliverables |
|------------|--------------|
| **Inception** | Stakeholder Register, Vision Document |
| **Elaboration** | Use Cases, NFRs, Data Dictionary |
| **Construction** | UAT Test Cases, Process Flows |
| **Transition** | Final Documentation, Training Materials |

## 🔗 Related Projects

These documentation templates complement technical implementations:

- [digital-banking-api-demo](https://github.com/hafeez-learn/digital-banking-api-demo) - REST microservices
- [audit-notification-service](https://github.com/hafeez-learn/audit-notification-service) - Event-driven architecture
- [k8s-observability-stack](https://github.com/hafeez-learn/k8s-observability-stack) - Kubernetes infrastructure

## 💡 Tips for System Analysts

1. **Be Specific** — Vague requirements lead to rework
2. **Include Examples** — Real data helps developers understand intent
3. **Trace Everything** — Requirements → Use Cases → Test Cases should be linked
4. **Review Regularly** — Documentation rots; keep it current
5. **Get Sign-off** — All stakeholders should approve requirements

## 📝 Template Standards Used

- **IEEE 830** - Software Requirements Specifications
- **IIBA BABOK** - Business Analysis Body of Knowledge
- **Agile Manifesto** - User story principles
- **INVEST** - User story quality checklist

## 🤝 Contributing

Feel free to add your own templates or improve existing ones.

## 📄 License

MIT License
