# HealthSpeak AI - Software Requirements Specification

## 1. Introduction

### 1.1 Purpose
This document details the software requirements for the HealthSpeak AI system that enables patients and healthcare staff to retrieve exact laboratory test results from electronic medical records using natural language queries.

### 1.2 Scope
This SRS defines the functional and non-functional requirements, architectural constraints, system interfaces, and behavior for a cloud-based conversational AI system integrating Google Cloud Run, Firestore, and Google Gemini AI.

---

## 2. Overall Description

### 2.1 Product Functions
- Accept natural language queries from patients and healthcare staff
- Query Firestore database for laboratory data
- Generate clear, exact-value responses via Google Gemini AI
- Support single and multiple lab value queries
- Ensure compliance with HIPAA and data privacy regulations

### 2.2 User Classes and Characteristics
- Patients (non-technical users)
- Healthcare Facility Staff (medical and admin professionals)
- Healthcare IT Admins (technical experts)

### 2.3 Operating Environment
- Deployed on Google Cloud Run serverless infrastructure
- Uses Firestore for NoSQL database storage
- Interfaced with Google Gemini AI for language inference
- Accessible via web and potentially integrated applications

---

## 3. Specific Requirements

### 3.1 Functional Requirements

| Req ID | Description                                                                                  |
|--------|----------------------------------------------------------------------------------------------|
| FR1    | Accept natural language questions about lab results                                         |
| FR2    | Retrieve exact lab result values and test dates from Firestore                              |
| FR3    | Return single lab result in a clear formatted response                                      |
| FR4    | Return multiple or all lab results as formatted numbered list                               |
| FR5    | Provide error messages when requested data is unavailable                                  |
| FR6    | Support queries from both patients and healthcare staff                                    |
| FR7    | Maintain data privacy and HIPAA compliance                                                 |

### 3.2 Non-Functional Requirements

| Req ID | Description                                                                                  |
|--------|----------------------------------------------------------------------------------------------|
| NFR1   | System responses must be delivered within 3 seconds (95th percentile)                       |
| NFR2   | System must scale automatically under varying loads                                        |
| NFR3   | System must respond only with exact clinical data without medical advice                    |
| NFR4   | Maintain availability above 99.9%                                                          |
| NFR5   | Log user queries and system responses securely                                             |

### 3.3 System Interfaces

- Webhook/API endpoint for receiving user queries
- Firestore database for retrieving lab results
- Google Gemini AI API for language generation

---

## 4. System Features

### 4.1 Natural Language Query Processing

- Input: Free text query about lab results
- Output: Clear, precise lab result responses
- Details: Employ Google Gemini AI model in a RAG architecture

### 4.2 Data Retrieval

- Firestore queried for patient's lab data document
- Structured lab results stored as JSON key-value pairs with test dates

### 4.3 Response Formatting

- Single lab test queries return a concise sentence
- Multiple or 'all' lab tests return numbered list with results

### 4.4 Error Handling
- Inform user when specific lab data is not found
- Suggest available lab tests for querying

---

## 5. Performance Requirements

- Response latency below 3 seconds for 95% of requests
- Support concurrent queries scaling to healthcare facility peak loads

---

## 6. Design Constraints

- Must utilize Google Cloud serverless services for deployment
- Must maintain strict HIPAA compliance regarding patient PHI data
- Must limit output to quoting stored lab data; no inference beyond data

---

## 7. Quality Attributes

- Usability: Easy to interact with for patients and staff  
- Scalability: Automatic scaling via Cloud Run  
- Security: HIPAA-compliant data handling  
- Maintainability: Modular design with n8n workflow orchestration  

---

## 8. Glossary

Same as URS.

---

## 9. References

- Google Cloud HIPAA Compliance  
- Google Gemini AI Developer Guide  
- Firestore Security Best Practices  
