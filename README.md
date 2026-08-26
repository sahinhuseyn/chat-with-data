# 💬 Chat with Your Data

> Query any dataset using plain language — no SQL knowledge required.

[![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)](https://python.org)
[![Groq](https://img.shields.io/badge/LLM-Groq%20%7C%20Llama%203.3-orange)](https://groq.com)
[![Streamlit](https://img.shields.io/badge/UI-Streamlit-red?logo=streamlit)](https://streamlit.io)
[![PostgreSQL](https://img.shields.io/badge/DB-PostgreSQL-336791?logo=postgresql)](https://postgresql.org)

---

## 🧠 What it does

**Chat with Your Data** is an AI-powered text-to-SQL platform that lets anyone — regardless of technical background — ask questions about their data in plain language and receive instant, accurate answers.

Upload a CSV, connect a PostgreSQL database, or paste a SQL file — then simply ask:

> *"Which product had the highest revenue last quarter?"*
> *"How many users registered in October?"*
> *"Show me the top 5 customers by total spend."*

The system converts your question into SQL, executes it safely, and explains the result in plain language.

---

## ✨ Features

- **Natural Language → SQL** — Schema-aware query generation via Groq API (Llama 3.3-70B)
- **Multi-source support** — CSV, Excel, SQLite, raw `.sql` files, and live PostgreSQL connections
- **Automated Data Quality Report** — detects nulls, negative values, anomalous entries, and duplicate rows
- **Multi-table support** — handles JOINs across multiple tables automatically
- **Read-only execution** — all destructive operations (INSERT, UPDATE, DELETE, DROP) are blocked at the prompt level
- **Plain-language explanations** — results are summarized in human-readable text alongside the data table

---

## 🏗️ Architecture

```
User Input (natural language)
        │
        ▼
Schema Extractor  ──►  Prompt Builder
                              │
                              ▼
                    Groq API (Llama 3.3-70B)
                              │
                              ▼
                    SQL Query Generator
                              │
                    ┌─────────┴──────────┐
                    ▼                    ▼
             SQLite Engine       PostgreSQL Engine
                    │                    │
                    └─────────┬──────────┘
                              ▼
                    Result + AI Explanation
                              │
                              ▼
                      Streamlit UI
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| LLM | Groq API — Llama 3.3-70B |
| Backend | Python, Flask |
| UI | Streamlit |
| Databases | PostgreSQL, SQLite |
| Data Processing | Pandas, NumPy |
| Prompt Engineering | Custom schema-aware system prompts |

---

## 🚀 Run Locally

### 1. Clone the repo
```bash
git clone https://github.com/sahinhuseyn/chat-with-your-data.git
cd chat-with-your-data
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Set up environment variables
```bash
cp .env.example .env
# Add your GROQ_API_KEY to .env
```

### 4. Run
```bash
streamlit run app.py
```

---

## 📁 Project Structure

```
chat-with-your-data/
├── app.py                  # Streamlit entry point
├── core/
│   ├── llm.py              # Groq API integration
│   ├── sql_engine.py       # Query execution & safety checks
│   ├── schema_extractor.py # DB schema parsing
│   └── data_quality.py     # Automated DQ checks
├── assets/
│   └── demo.png
├── .env.example
├── requirements.txt
└── README.md
```

---

## 🔒 Security

- Only `SELECT` statements are permitted — enforced at the prompt and execution layer
- No data is stored or transmitted beyond the local session
- PostgreSQL credentials are passed via environment variables, never hardcoded

---

## 📸 Demo

![Demo](assets/demo.png)

---

## 👤 Author

**Sahin Huseynov** — [LinkedIn](https://linkedin.com/in/sahinhuseynov) · [GitHub](https://github.com/sahinhuseyn)
