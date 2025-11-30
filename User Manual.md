# HealthSpeak AI - User Manual

## 1. Introduction

HealthSpeak AI is a conversational assistant that helps patients and healthcare staff understand laboratory test results by quoting exact data from electronic medical records in Firestore.

---

## 2. Getting Started

### 2.1 Accessing the System

- Access the HealthSpeak AI interface via a web chat or messaging platform integrated with the n8n chatbot webhook URL.
- No special login is required in the demo version; users are identified by their patient IDs.

### 2.2 Asking Questions

- Type natural language questions about your lab results, for example:
  - "What is my HbA1c?"
  - "Show all my lab results"
  - "What is my fasting blood sugar?"
- The assistant will respond with exact test values and dates from your medical records.

---

## 3. Using HealthSpeak AI

### 3.1 Typical Queries

| Query Example               | Expected Response Format                                 |
|----------------------------|---------------------------------------------------------|
| "What is my HbA1c?"          | "HbA1c: 5.8% (Jul 6, 2025) from your medical records."   |
| "Show all my lab results"    | Numbered list of lab tests and values with dates         |
| "Patient 005 cholesterol?"   | "Total Cholesterol: 227 mg/dL (Jul 6, 2025)"             |

### 3.2 Limitations and Notes

- HealthSpeak AI only quotes lab data; it does not provide any diagnosis, advice, or interpretation.
- Responses are based on the available data in your medical records.
- If a lab test is missing, the system will notify you and suggest available tests.

---

## 4. Troubleshooting

| Issue                         | Possible Cause                   | Solution                                |
|-------------------------------|---------------------------------|----------------------------------------|
| No response or timeout         | Network or server issue          | Retry after some time; contact support |
| Incorrect or missing lab data  | Data not available in Firestore  | Verify patient ID and data completeness |
| Unexpected output or errors    | Temporary system error           | Restart workflow or report to technical team |

---

## 5. Security and Privacy

- All patient data is handled according to HIPAA compliance regulations.
- Data access is controlled and logged.
- No personal data is shared beyond the scope of your queries.
