# HealthSpeak AI - Test Plan

## 1. Introduction

This test plan outlines the testing strategy, objectives, scope, resources, and schedule for verifying the functionality, performance, and compliance of the HealthSpeak AI system.

---

## 2. Test Objectives

- Verify that the system returns accurate laboratory data responses matching Firestore records.
- Ensure natural language queries in English are correctly processed by Gemini AI.
- Confirm formatting rules for single and multiple lab results are followed.
- Validate error handling for unavailable or malformed queries.
- Verify response times meet performance criteria.
- Ensure system behaviors comply with HIPAA and privacy standards.

---

## 3. Scope

### In-Scope

- Functional testing of chat trigger, AI agent logic, Firestore data retrieval, and Gemini responses.
- Performance testing of response latency.
- Usability testing for clarity and readability of responses.
- Security checks for data access authorization and privacy compliance.

### Out-of-Scope

- End-to-end integration with live EMR systems.
- Authentication and authorization testing (future scope).
- Multi-language or localization testing.

---

## 4. Test Items

- Chat Trigger Node
- AI Agent Node and system message
- Firestore Lookup Tool
- Google Gemini Chat Model Node
- Webhook API interface

---

## 5. Testing Types and Techniques

| Test Type        | Description                                            | Methods                   |
|------------------|--------------------------------------------------------|---------------------------|
| Functional       | Validate correct retrieval and formatting of lab data  | Manual testing, automated scripts |
| Performance      | Measure response times under different loads           | Load testing, benchmarking |
| Usability        | Assess clarity of responses and user interaction       | User feedback, heuristic review |
| Security         | Verify data privacy and proper data access control      | Code review, penetration testing |

---

## 6. Test Cases (Sample)

| ID    | Description                                   | Input                                    | Expected Output                                                         | Result (Pass/Fail) |
|-------|-----------------------------------------------|------------------------------------------|--------------------------------------------------------------------------|--------------------|
| TC001 | Query single lab result                      | "What is my HbA1c?" (patient_001)        | "HbA1c: 5.8% (Jul 6, 2025) from your medical records."                  |                    |
| TC002 | Query multiple/all lab results               | "Show all my lab results" (patient_001)  | Numbered list with all lab results and dates                            |                    |
| TC003 | Query unknown test                           | "What is my Vitamin D level?" (patient_001) | Error message listing available tests                                 |                    |
| TC004 | Measure response latency                     | Any valid query                          | Response time < 3 seconds                                               |                    |
| TC005 | Verify no diagnosis or advice generated     | Any query related to medical advice     | Responses contain only quoted lab data, no advice or diagnosis         |                    |
| TC006 | Healthcare staff query for specific patient | "Patient 005 cholesterol?"                 | Formatted lab value suitable for patient communication                 |                    |

---

## 7. Test Environment

- Google Cloud Platform with Firestore and Cloud Run enabled
- n8n workflow deployed to Cloud Run
- Gemini AI access via API credentials
- Synthetic patient data seeded in Firestore

---

## 8. Entry and Exit Criteria

### Entry Criteria

- All development code deployed and stable
- Firestore seeded with demo data
- Test environment configured
- Test cases approved

### Exit Criteria

- All critical and high-severity defects fixed and verified
- Test coverage > 90% of functional requirements
- Performance targets met

---

## 9. Roles and Responsibilities

| Role             | Responsibility                      | Name      |
|------------------|-----------------------------------|-----------|
| Test Lead        | Manage testing activities          |           |
| QA Engineers     | Execute test cases, report defects|           |
| Developers       | Fix issues, support testing        |           |
| Product Owner    | Approve test deliverables          |           |
