# HealthSpeak AI - Deployment Plan

## 1. Introduction

This document outlines the steps and considerations required for deploying the HealthSpeak AI workflow and supporting infrastructure to a production environment.

---

## 2. Deployment Overview

HealthSpeak AI is deployed as an n8n workflow running on Google Cloud Run. It integrates with Firestore for data storage and Google Gemini AI for language generation. The deployment plan covers initial setup, configuration, and operational readiness.

---

## 3. Deployment Steps

### 3.1 Prerequisites

- Google Cloud project with billing enabled
- APIs enabled: Cloud Run, Firestore, Vertex AI (Gemini)
- IAM roles: Appropriate permissions for deployment and access
- Firestore seeded with synthetic patient lab data

### 3.2 Deployment Procedure

1. **Upload and configure n8n workflow**  
   Import the HealthSpeak AI workflow JSON into n8n instance.

2. **Deploy n8n to Cloud Run**  
   Use Google Cloud Console or CLI to deploy n8n container with appropriate resource settings (CPU, memory).

3. **Configure environment variables**  
   Set environment variables including Gemini API credentials and Firestore project ID.

4. **Set up Firestore access**  
   Ensure service account used by Cloud Run has read permissions on Firestore collection.

5. **Enable Gemini AI integration**  
   Confirm API keys and access are configured within n8n Gemini Chat Model node.

6. **Testing and validation**  
   Run smoke tests—send queries to chat webhook and verify responses.

7. **Monitoring setup**  
   Configure Cloud Run logging and monitoring dashboards.

---

## 4. Rollout Strategy

- Initial deployment to staging environment for validation.
- Progressive rollout to production after UAT sign-off.
- Ability to rollback to previous deployment on issues.

---

## 5. Backup and Recovery

- Regular backup schedules for Firestore database.
- Workflow version control via n8n templates and Git.
- Disaster recovery plan to restore Firestore and redeploy workflow.

---

## 6. Operational Responsibilities

| Role           | Responsibility                      |
|----------------|-----------------------------------|
| DevOps Engineer| Manage deployment and scaling      |
| System Admin    | Monitor service health             |
| Support Team    | Handle incidents and user issues   |

---

## 7. Security Considerations

- Secure storage of API keys and credentials.
- Least privilege principles for service accounts.
- Regular audits on Firestore access logs.
