# 🩺 AI Nurse Assistant — Annotation Guidelines

## 📘 Overview

This guideline is for annotating user messages to train an AI nurse assistant that can:
- Recognize symptoms
- Offer care guidance
- Answer general health questions

---

## 📦 Data Schema

Each annotated message must follow this format:

| Field        | Type    | Description                                                  |
|--------------|---------|--------------------------------------------------------------|
| `input`      | string  | The user’s original message                                  |
| `response`   | string  | The assistant's suggested or generated reply                 |
| `intent`     | string  | The purpose behind the user’s message                        |
| `entities`   | list    | Keywords or phrases related to symptoms, conditions, etc.    |
| `sentiment`  | string  | Detected emotion: `positive`, `neutral`, or `negative`       |
| `meta`       | object  | Additional metadata, such as age, gender, and timestamp                           |
---

## 🎯 Intent Annotation

### What is **Intent**?
Intent is the user’s goal—what they want the assistant to do.

### ✅ Supported Intents

| Intent               | Description                                                                 | Example |
|----------------------|-----------------------------------------------------------------------------|---------|
| `report_symptom`     | User shares symptoms without asking for guidance                            | "I have a headache and chills." |
| `ask_health_guidance`| User asks what to do about a symptom or whether to see a doctor             | "Should I go to the doctor or rest?" |
| `ask_medical_info`   | User asks for general medical or health info (not personal)                 | "What causes dehydration?" |
| `share_health_status`| User shares a background condition or long-term health issue                | "I have asthma." |
| `ask_medication_info`| User asks about medication side effects or usage (not for prescriptions)    | "Can I take ibuprofen on an empty stomach?" |
| `confirm_understanding`| User agrees or acknowledges a suggestion                                  | "Got it, thank you!" |
| `deny_suggestion`    | User rejects or disagrees with the advice                                   | "That didn’t help at all." |
| `greeting`           | User says hello or starts the conversation                                  | "Hi there!" |
| `goodbye`            | User ends the conversation                                                   | "Thanks, bye!" |
| `other`              | Any message that doesn’t fit the above categories                           | "I like your voice." |

---

## 🧩 Entity Annotation

### What are **Entities**?
Entities are important health-related keywords or phrases in the user’s message, such as:

- Symptoms (e.g., "fever", "nausea")
- Conditions (e.g., "diabetes")
- Body parts (e.g., "throat", "chest")
- Time expressions (e.g., "for two days")
- Everyday care terms (e.g., "rest", "hydrate")
- Medication names (e.g., "Panadol")

### 📝 Guidelines
- Use **exact phrases** from the text.
- Be specific; don’t include generic words like “feel” or “sick” on their own.
- Use **lowercase** unless it’s a proper name.

#### ✅ Examples

| Input                                                       | Entities                            |
|-------------------------------------------------------------|-------------------------------------|
| "I have a sore throat and a runny nose."                    | `["sore throat", "runny nose"]`     |
| "How long should I rest if I have a fever?"                 | `["rest", "fever"]`                 |
| "I took Panadol 4 hours ago."                               | `["Panadol", "4 hours ago"]`        |
| "My daughter is coughing a lot at night."                   | `["coughing", "night"]`             |

---

## 😊 Sentiment Annotation

### What is **Sentiment**?
Sentiment describes the user’s emotional tone in the message.

| Sentiment  | When to Use                                                    | Example |
|------------|----------------------------------------------------------------|---------|
| `positive` | Calm, appreciative, or satisfied tone                          | "Thanks, that helps a lot!" |
| `neutral`  | Factual, emotionless, or unclear tone                          | "I have a headache." |
| `negative` | Worried, upset, or showing discomfort or frustration           | "I feel terrible. It won't stop hurting." |

> If unsure, choose `neutral`.

---

## 🔍 Sample Annotations

### Example 1
```json
{
  "input": "I've had a bad cough for three days.",
  "response": "It sounds like you've been dealing with a persistent cough. Try to stay hydrated and rest. If it doesn’t improve, consider speaking with a doctor.",
  "intent": "report_symptom",
  "entities": ["cough", "three days"],
  "sentiment": "negative"
}
