# LLM RAG Contract Analyzer – System Architecture

## 🧠 Overview
This project implements a local **Retrieval-Augmented Generation (RAG)** system using **LLaMA 3** for analyzing contract documents. It combines **Natural Language Processing (NLP)** techniques to extract intent from legal text and a **vector-based search** to retrieve relevant clauses for question answering.

The architecture is designed for local execution to reduce costs while providing a scalable blueprint for enterprise deployment via **AWS Bedrock**.

---

## 📊 System Workflow

1. **Document Ingestion**
   - PDFs are uploaded to the `data/sample_contracts/` folder.
   - Text is extracted using `pdfplumber` or `PyMuPDF` for efficient parsing.

2. **Intent Extraction (NLP Preprocessing)**
   - **BERT**, **BART**, or **Pegasus** identifies key clauses and legal intents.
   - Named Entity Recognition (NER) is used to detect entities like dates, amounts, and parties.

3. **Vector Index Creation**
   - Each clause or paragraph is transformed into embeddings using Hugging Face models.
   - **FAISS** (or **Chroma**) is used to store and query the vector database.

4. **RAG Pipeline Execution**
   - User queries are embedded and matched against the indexed contracts.
   - Relevant sections are retrieved and provided as context to **LLaMA 3**.

5. **LLM Response Generation**
   - LLaMA 3 generates responses, grounded in the retrieved contract information.
   - The Python interface provides a chat-like experience for interacting with the contracts.

---

## 🗂️ Technical Components

| Component                 | Technology/Model                  | Purpose                                |
|---------------------------|-----------------------------------|----------------------------------------|
| **LLM Model**             | LLaMA 3 (via Hugging Face)        | Generate responses grounded in context |
| **NLP Models**            | BERT / BART / Pegasus             | Extract legal intents and summarize    |
| **PDF Parsing**           | pdfplumber / PyMuPDF              | Ingest contract documents              |
| **Vector Search**         | FAISS / Chroma                    | Index and retrieve document chunks     |
| **Interface**             | Python (CLI-based)                | User-friendly chat with the LLM        |

---

## 📐 Architectural Diagram

```plaintext
            User Query
                │
                ▼
        ┌──────────────────┐
        │ Python Interface │
        └──────────────────┘
                │
                ▼
   ┌───────────────────────────┐
   │   1. PDF Ingestion        │
   └───────────────────────────┘
                │
                ▼
   ┌───────────────────────────┐
   │   2. Intent Extraction    │
   └───────────────────────────┘
                │
                ▼
   ┌───────────────────────────┐
   │   3. Vector Index (FAISS) │
   └───────────────────────────┘
                │
                ▼
   ┌───────────────────────────┐
   │   4. RAG Pipeline         │
   └───────────────────────────┘
                │
                ▼
   ┌───────────────────────────┐
   │   5. LLaMA 3 Response     │
   └───────────────────────────┘
                │
                ▼
       Interactive Output to User
```

## 🌐 Business Use Case & Future Scalability

This system can be extended to enterprise-level deployments on AWS Bedrock, providing scalable, secure contract intelligence. Possible applications include:

1. **Contract Compliance Checks** – Identify missing clauses, dates, or obligations.
2. **Legal Document Summarization** – Quickly extract key insights from lengthy contracts.
3. **Customer Support Automation** – Automate responses to contract-related queries.

## 🔮 Future Enhancements:

- Integrate `LangChain` for modular RAG workflows.
- Deploy on `AWS Bedrock` for production use.
- Add `multi-document` ingestion and cross-document queries.

## 📌 Why This Matters

- **Cost Efficiency**: Local LLaMA 3 keeps operational costs minimal.
- **Scalability**: Easily extend to AWS Bedrock for enterprise solutions.
- **AI Innovation**: Demonstrates cutting-edge RAG techniques with real business value.