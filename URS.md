# HealthSpeak AI - User Requirements Specification

## 1. Document Information

**Document Title:** HealthSpeak AI User Requirements Specification  
**Version:** 1.1  
**Date:** November 30, 2025  
**Author:** Donni  
**Status:** Draft

## 2. Introduction

### 2.1 Purpose
HealthSpeak AI addresses the common challenge faced by patients and healthcare facilities when trying to understand and communicate laboratory test results. Medical laboratory reports contain technical terms, units of measurement, and reference ranges that are difficult for non-medical professionals to interpret. This system provides a conversational interface that allows patients to ask questions about their lab results in natural language and receive exact values quoted directly from their electronic medical records.

### 2.2 Scope
The system scope includes:
- Natural language processing of patient queries about laboratory results
- Retrieval of exact laboratory test values and dates from electronic medical records
- Generation of clear, patient-friendly responses containing only verified data
- Support for both single test queries and requests for multiple/all results
- Healthcare facility staff assistance for patient communication

**Out of scope:**
- Medical diagnosis or clinical interpretation
- Treatment recommendations or lifestyle advice
- Authentication and patient identity verification (demo version)
- Integration with hospital EMR systems

## 3. User Profiles

### 3.1 Primary Users

**Patient** - Individuals seeking to understand their own laboratory test results
- Characteristics: Non-medical background, limited technical terminology knowledge
- Needs: Simple explanations of lab values, exact numbers with dates, no medical jargon
- Usage Context: Personal smartphone access, patient portal integration

**Healthcare Facility Staff** - Nurses, medical assistants, administrative staff assisting patients
- Characteristics: Healthcare training, patient-facing communication role
- Needs: Quick lookup of patient lab results, clear communication format for patients
- Usage Context: Front desk, clinic stations, telehealth consultations

### 3.2 Secondary Users

**Healthcare IT Administrator** - Technical staff managing the system
- Characteristics: Familiar with cloud infrastructure and workflow automation
- Needs: Easy deployment, monitoring, and maintenance capabilities
- Usage Context: System administration, performance monitoring

**Clinic Manager** - Healthcare facility leadership overseeing patient experience
- Characteristics: Business and operations focus, patient satisfaction metrics
- Needs: System reliability, usage analytics, integration potential
- Usage Context: Operational oversight, patient satisfaction improvement

## 4. User Requirements

### 4.1 Functional Requirements (FR)

**FR-001: Natural Language Query Processing**
- The system SHALL accept questions in conversational English about laboratory test results
- Examples: "What is my HbA1c?", "Show all my lab results", "Cholesterol level?"

**FR-002: Exact Data Retrieval**
- The system SHALL retrieve laboratory test values and test dates exactly as stored in the medical record database
- The system SHALL NOT generate, estimate, or modify laboratory values

**FR-003: Single Test Response**
- The system SHALL respond to specific test queries with: "[Test Name]: [Value] ([Date]) from your medical records."

**FR-004: Multiple Test Response**
- The system SHALL format responses to "all results" or multiple test queries as numbered lists
- Each item SHALL include test name, value, date, and source attribution

**FR-005: Data Transparency**
- The system SHALL clearly indicate that responses come from medical records
- The system SHALL use consistent phrasing: "from your medical records"

**FR-006: Error Handling**
- The system SHALL respond gracefully when requested test data is unavailable
- Response SHALL list available tests when appropriate

**FR-007: Healthcare Staff Support**
- The system SHALL support staff queries like "Patient John Doe HbA1c?" for patient communication
- The system SHALL provide consistent formatting suitable for reading aloud to patients

### 4.2 Non-Functional Requirements (NFR)

**NFR-001: Response Time**
- The system SHALL respond to queries in less than 3 seconds (95th percentile)

**NFR-002: Language**
- The system SHALL respond in clear, simple English suitable for non-medical users and staff communication

**NFR-003: Safety**
- The system SHALL NOT provide medical diagnosis, interpretation, or advice
- The system SHALL NOT classify results as normal/abnormal
- The system SHALL NOT recommend treatments or lifestyle changes

**NFR-004: Scalability**
- The system SHALL handle concurrent patient queries without degradation
- The system SHALL support healthcare facility peak usage periods

**NFR-005: Data Privacy**
- The system SHALL handle patient data according to privacy regulations
- The system SHALL log access for audit purposes (future requirement)

**NFR-006: Multi-User Support**
- The system SHALL support concurrent usage by patients and healthcare staff
- The system SHALL maintain response consistency across user types

## 5. User Stories

**As a patient, I want to:**
- US-001: Ask "What is my HbA1c?" and get the exact value with date
- US-002: Ask "Show all my results" and get a clear numbered list
- US-003: Ask about unavailable tests and get helpful guidance

**As a healthcare facility staff member, I want to:**
- US-004: Quickly check "Patient ID 005 HbA1c?" to communicate with patients
- US-005: Get formatted results I can read directly to patients over phone
- US-006: Access multiple patient results efficiently during busy clinic hours

**As a healthcare IT admin, I want to:**
- US-007: Deploy the system quickly on cloud infrastructure
- US-008: Monitor system performance and usage across facility departments

**As a clinic manager, I want to:**
- US-009: Improve patient satisfaction through easy lab result access
- US-010: Track system usage to justify healthcare IT investments

## 6. Acceptance Criteria

**AC-001:** System correctly quotes HbA1c value and date from demo patient record
**AC-002:** "Show all results" produces numbered list format with 5+ lab tests
**AC-003:** Response time consistently under 3 seconds for all test cases
**AC-004:** No medical interpretation appears in any response
**AC-005:** Error handling provides clear guidance when data unavailable
**AC-006:** Healthcare staff test case: "Patient 005 cholesterol" returns correct formatted result

## 7. Assumptions and Constraints

**Assumptions:**
- Demo uses synthetic patient data
- Single patient context for initial version
- English language queries and responses
- Healthcare facilities have basic cloud infrastructure access

**Constraints:**
- Limited to laboratory blood test results only
- No real patient authentication in demo version
- Cloud-based deployment only

## 8. Glossary

| Term | Definition |
|------|------------|
| EMR | Electronic Medical Record |
| HbA1c | Hemoglobin A1c blood test |
| RAG | Retrieval-Augmented Generation |
| HIPAA | Health Insurance Portability and Accountability Act |
