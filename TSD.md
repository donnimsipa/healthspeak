# HealthSpeak AI - Technical Specification Document

## 1. Introduction

This Technical Specification Document details the architecture, technologies, interfaces, and implementation details for the HealthSpeak AI system, a conversational AI assistant for patient lab results.

---

## 2. System Architecture Overview

The system consists of:

- **n8n Workflow Engine**: Orchestrates the conversational flow and integrates external tools.
- **Webhook Chat Trigger**: Entry point for user queries.
- **Google Cloud Firestore**: NoSQL database storing synthetic patient lab results.
- **Google Gemini AI**: Generative AI for natural language response generation.
- **AI Agent Node**: Manages interaction between user input, Firestore lookup, and Gemini model.

---

## 3. Technology Stack

| Component                 | Technology                          | Description                             |
|---------------------------|-----------------------------------|---------------------------------------|
| Workflow Orchestration    | n8n (serverless on Cloud Run)     | Visual low-code workflow management   |
| Cloud Compute             | Google Cloud Run                   | Managed serverless container platform |
| Database                  | Google Firestore                  | NoSQL document database for lab data  |
| AI Language Model         | Google Gemini (Vertex AI)         | Large language model for generation   |
| Authentication (future)   | Google Identity Platform          | Identity and access management         |

---

## 4. Detailed Components

### 4.1 n8n Workflow

- Handles incoming chat messages via webhook.
- Executes AI Agent node configured with system message rules.
- Calls Firestore tool to retrieve patient lab data.
- Passes user inputs and retrieved data to Gemini model.
- Returns formatted responses to users.

### 4.2 Firestore Data Model

- Collection: `healthspeak`
- Document: `patients`
- Sample fields:
  - Lab tests stored as key-value pairs inside a JSON object.
  - Values include test result and timestamp as a string.

### 4.3 Google Gemini AI Model Integration

- Uses the official Gemini Chat Model node in n8n.
- Provides system prompts to enforce:
  - Quote-only lab data behavior.
  - English language output.
  - Format standardization.
- Receives context data from Firestore for accurate responses.

---

## 5. API Specifications

### 5.1 Webhook Endpoint

- URL: Configurable n8n Cloud Run webhook URL
- Method: HTTP POST
- Payload:

```
{
  "question": "<user question string>",
  "patient_id": "<optional patient identifier>"
}
```

- Response:

```
{
  "answer": "<natural language lab data response>"
}
```

---

## 6. Security and Privacy

- Firestore permissions restricted via service accounts.
- HIPAA compliance maintained by strict data quoting and no inference.
- Logs maintained for audit purposes (future implementation).

---

## 7. Deployment Details

- n8n workflow deployed on Google Cloud Run container.
- Firestore database seeded with synthetic patient data.
- Gemini API credentials stored securely as environment variables.
- Workflow nodes configured for retries and error handling.

---

## 8. Operational Considerations

- Monitor Cloud Run autoscaling and cold start latency.
- Monitor Firestore read latency and access patterns.
- Track Gemini API usage quotas and costs.
- Back up Firestore data regularly.
