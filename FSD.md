## 1. Overview

This document specifies the detailed functional behavior of the HealthSpeak AI system designed to provide patients and healthcare facility staff with exact laboratory test results via natural language queries.

---

## 2. Functionality

### 2.1 User Interaction

- **Entrypoint:**  
  Users initiate queries through a webhook-enabled chat interface (e.g., a web chat or messaging platform).

- **Input:**  
  Natural language messages containing questions about lab results.

- **Output:**  
  Clear, concise responses quoting exact lab results and test dates, formatted appropriately.

### 2.2 Query Processing

- System receives user text.
- Passes the text to the AI Agent node.
- AI Agent evaluates the question against available lab data.
- If patient data required, AI Agent calls Firestore lookup tool to fetch lab results.
- AI Agent constructs a prompt combining system instructions, patient data, and user question.
- Google Gemini AI generates a natural language answer.

### 2.3 Lab Data Handling

- Lab results stored in Firestore as JSON with keys like HbA1c, Hemoglobin, Cholesterol, Triglycerides, Fasting Blood Sugar.
- Each test value paired with a date string.
- Lab data acts as the single source of truth.

### 2.4 Response Formatting

- Single lab test query → response in format:  
  "[Test Name]: [Value] ([Date]) from your medical records."
- Multiple or all tests query → response as numbered list:  
  1. Test1: Value1 (Date1)  
  2. Test2: Value2 (Date2)  
  ...
- When data is not found, respond politely and list available tests.

### 2.5 Error Handling

- Missing data triggers a friendly error message.
- Malformed queries receive a prompt to clarify.
- API failures return a generic error message advising retry.

---

## 3. Components & Nodes

| Component                        | Description                                     |
|---------------------------------|------------------------------------------------|
| Chat Trigger Node                | Receives initial user chat messages            |
| AI Agent Node                   | Applies system rules, manages tool access       |
| Firestore Lookup Tool           | Retrieves patient lab data from Firestore       |
| Google Gemini Chat Model Node   | Generates natural language responses            |

---

## 4. Sequence Flow

1. User sends chat message.
2. Chat Trigger receives and launches workflow.
3. AI Agent parses message, triggers Firestore lookup if needed.
4. Firestore returns lab results JSON.
5. AI Agent sends prompt and data to Gemini.
6. Gemini returns natural language response.
7. Response sent back to user.

---

## 5. Data Models

### Patient Lab Results (example JSON)

```
{
  "HbA1c": "5.8% (Jul 6, 2025)",
  "Hemoglobin": "13.2 g/dL (Jul 6, 2025)",
  "Total Cholesterol": "227 mg/dL (Jul 6, 2025)",
  "Triglycerides": "227 mg/dL (Jul 6, 2025)",
  "Fasting Blood Sugar": "131 mg/dL (Jul 6, 2025)"
}
```

---

## 6. Constraints and Limitations

- No medical diagnosis or advice offered.
- Limited to lab data quoting, no interpretation.
- Designed for English-language queries/responses.
- Initial demo limited to a single patient context.

---

## 7. Future Functional Enhancements (non-mandatory)

- Patient authentication and multi-patient support
- Multilingual support (e.g., Indonesian)
- Expanded query scope to vitals, medications
- Integration with hospital EMR systems