# HealthSpeak AI

## Why HealthSpeak AI?

Are you frustrated with navigating complex menus and typing tedious search queries just to find a patient's laboratory results? Healthcare providers and patients alike often face this challenge, leading to wasted time and miscommunication. HealthSpeak AI was created to eliminate these barriers by offering a simple conversational interface that instantly retrieves and clearly explains exact lab results, removing the hassle of manual searching.

***

## Story

HealthSpeak AI began as a solution to a common pain point in healthcare: accessing and understanding lab data quickly and accurately. Instead of overwhelming users with complex interfaces or ambiguous interpretations, this system uses generative AI to quote exact lab values directly from electronic medical records. By leveraging an orchestrated workflow on Google Cloud Run, Firestore, and Google Gemini AI, HealthSpeak AI delivers precise, trustworthy data in natural language — empowering patients and healthcare professionals to communicate lab results effortlessly.

***

## Overview

HealthSpeak AI is a patient-facing conversational assistant designed to help users understand their laboratory test results through natural language queries. The system provides exact lab values directly quoted from electronic medical record data, without interpretation or medical advice.

### Key Features

- Natural language questions like "What is my HbA1c?" or "Show all my lab results"
- Uses n8n workflow to connect chat trigger, Firestore database, and Gemini AI
- Outputs only verifiable lab data with dates, avoiding medical advice
- Supports patients and healthcare staff for efficient result communication
- Runs serverless on Google Cloud Run for easy scaling and maintenance

***

## How It Works

1. User sends a question to the chat interface.
2. The workflow triggers the AI Agent node which fetches patient lab data from Firestore.
3. AI Agent constructs a prompt following strict rules and sends it to Gemini AI.
4. Gemini returns a clear, exact quote of lab results, formatted as single lines or numbered lists depending on query scope.
5. The system displays the response in a user-friendly format.

***

## Limitations \& Next Steps

- Focused exclusively on data quoting; no clinical interpretation or recommendations.
- Demo version assumes single-patient context without user authentication.
- Planned expansions include multi-patient support, patient authentication, and multilingual capabilities.

## Project Artifacts

- [HealthSpeak Workflow JSON](healthspeak-ai.json)
- [User Requirements Specification (URS)](URS.md)
- [Software Requirements Specification (SRS)](SRS.md)
- [Functional Specification Document (FSD)](FSD.md)
- [Technical Specification Document (TSD)](TSD.md)
- [Test Plan](Test%20Plan.md)
- [User Acceptance Test (UAT)](UAT.md)
- [Deployment Plan](Deployment%20Plan.md)
- [User Manual](User%20Manual.md)
- [Maintenance Plan](Maintenance%20Plan.md)
