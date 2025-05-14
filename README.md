# 🧠 Mental Health Companion Dataset Repository

This repository contains annotated training data for the Mental Health Companion chatbot feature, designed to assist users experiencing health challenges by classifying their intent and extracting relevant information from text input.

---

## 📁 Repository Structure
```
Mental-Health-Companion/
│
├── data/
│ ├── raw/ # Raw collected text data
│ ├── annotated/ # Annotated data files (CSV/JSON)
│ │ ├── mental_health_batch1.csv
│ │ └── ...
│ ├── processed/ # Cleaned, labeled data
│ │ └── ...
│
├── notebooks/ # Jupyter notebooks for preprocessing/training
│ └── ...
|
├── schema/
│ └── text_schema.json # Data schema definition
│
├── scripts/ # Python scripts (e.g., for preprocessing)
│ └── ...
|
├── annotation_guidelines.md # Instructions for labeling intents, entities, etc.
│
└── README.md # This file
```
---

## 🧾 Data Schema

Each data entry follows this schema:

| Field         | Type     | Description                                 |
|---------------|----------|---------------------------------------------|
| input         | string   | Text input from user                        |
| response      | string   | Suggested or generated response             |
| intent        | string   | Purpose of the message (e.g., report_symptom, ask_info) |
| entities      | list     | Extracted keywords/phrases (e.g., ["anxiety"]) |
| sentiment     | string   | Detected sentiment: positive, neutral, negative |
| meta          | object   | Additional metadata (e.g., age, gender, timestamp) |

---

## 🏷️ Annotation Process

- Annotators label each user message with:
  - **Intent**: What is the user trying to do or express?
  - **Entities**: Key terms such as symptoms or conditions.
  - **Sentiment**: Emotional tone of the message.
  - **Meta Data**: Optional fields such as age, gender, and timestamp to enhance context.
- All annotations follow the [Annotation Guidelines](annotation/annotation_guidelines.md).

---

## 🧪 Example Entry

```json
{
  "user_input": "I can't sleep well at night.",
  "bot_response": "I'm sorry to hear that. Would you like to talk about your sleep habits?",
  "intent": "report_symptom",
  "entities": ["sleep"],
  "sentiment": "negative",
  "meta": {
    "age": 23,
    "gender": "male",
    "timestamp": null
  }
}
