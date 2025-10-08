# 📧 Email Classifier

## 🧠 Overview

The **Email Classifier** is an AI-powered NLP system that automatically analyzes incoming client or lead emails and classifies them based on intent, sentiment, and actionability.  
It helps automate sales workflows by identifying whether a response is **positive**, **negative**, **neutral**, **out-of-office**, or **needs follow-up** — enabling seamless CRM and marketing automation.

---

## 🚀 Features

- ✅ Classifies incoming emails into actionable categories:
  - Interested / Positive
  - Not Interested / Negative
  - Request for Info
  - Out-of-Office
  - Bounce / Auto-Reply
  - Referral or Redirect
- 🤖 Fine-tuned Transformer models (BERT, RoBERTa, or GPT-based)
- 🧹 Preprocessing pipeline that removes signatures and quoted replies
- 📊 Confidence scoring for human review when uncertainty is high
- 🔄 Integration-ready API (FastAPI/Flask)
- 💬 Optional AI Reply Generator integration for automated responses

---

## 🧩 System Architecture

```

Incoming Email
↓
Preprocessing Layer
↓
Text Embedding (SBERT / Transformer)
↓
Classifier Model (BERT / RoBERTa / Fine-tuned)
↓
Output Label (e.g. "Interested")
↓
Action Engine → Update CRM / Trigger Workflow

```

---

## ⚙️ Tech Stack

| Component      | Technology                              |
| -------------- | --------------------------------------- |
| Language       | Python 3.10+                            |
| NLP            | Hugging Face Transformers, spaCy        |
| Model Training | PyTorch / TensorFlow                    |
| Email Parsing  | `email-reply-parser`, `regex`, IMAP     |
| API Layer      | FastAPI / Flask                         |
| Database       | PostgreSQL / MongoDB                    |
| Integration    | CRM (HubSpot, Salesforce), Zapier / n8n |
| Deployment     | Docker + REST API                       |

---

## 📁 Project Structure

```

email-classifier/
│
├── data/
│ ├── raw_emails.csv
│ ├── labeled_emails.csv
│
├── src/
│ ├── preprocessing.py # Cleans and tokenizes emails
│ ├── model.py # Model loading and inference
│ ├── train.py # Fine-tuning scripts
│ ├── inference.py # Prediction logic
│ ├── api.py # REST API endpoint
│
├── notebooks/
│ └── experiments.ipynb # Model evaluation and EDA
│
├── requirements.txt
├── README.md
└── config.yaml

```

---

## 🧪 Example Usage

### 1️⃣ Run Inference

```python
from src.inference import classify_email

email_text = """
Hi, thanks for reaching out.
I’m interested to learn more about your pricing and product features.
"""
result = classify_email(email_text)
print(result)
# Output: {"label": "Interested", "confidence": 0.94}
```

### 2️⃣ Run via API

```bash
curl -X POST http://localhost:8000/classify \
  -H "Content-Type: application/json" \
  -d '{"email_text": "Can you send me your brochure?"}'
```

---

## 🧠 Model Training Overview

1. **Dataset Preparation**

   - Collect and label ~2–3k sample email replies
   - Example labels: `Interested`, `Not Interested`, `Out_of_Office`, `Info_Request`

2. **Fine-Tuning**

   - Use `bert-base-uncased` or `distilroberta-base`
   - Train for 3–5 epochs on labeled data

3. **Evaluation**

   - Metrics: Accuracy, F1-score, Precision, Recall
   - Optional: Confusion Matrix visualization

4. **Model Export**

   - Save as `.pt` or `.pkl`
   - Load via inference script or API

---

## 📬 Integration Examples

| System              | Action                                                 |
| ------------------- | ------------------------------------------------------ |
| **HubSpot CRM**     | Automatically update lead status based on email type   |
| **Gmail API**       | Read inbound emails and send replies                   |
| **Zapier / n8n**    | Connect classification results to automation workflows |
| **AI Reply System** | Generate smart follow-up emails using GPT-based models |

---

## 📊 Example Output

| Email Snippet                         | Predicted Label | Confidence |
| ------------------------------------- | --------------- | ---------- |
| “Sounds good, let’s schedule a call.” | Interested      | 0.95       |
| “No thanks, not relevant right now.”  | Not Interested  | 0.97       |
| “I’ll be back next week.”             | Out-of-Office   | 0.93       |
| “Can you share your brochure?”        | Info Request    | 0.89       |

---

## 🔒 Future Enhancements

- Multi-intent detection (“Not now, but contact later”)
- LLM-based summarization of replies
- Integration with WhatsApp and LinkedIn message parsing
- Reinforcement learning from user corrections
- Dashboard for analytics and classification metrics

---

## 🤝 Contributing

Contributions are welcome!
Please open a Pull Request with a clear description of your enhancement or bug fix.

---
