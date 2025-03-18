# LLM RAG Contract Analyzer
An end-to-end implementation of Retrieval-Augmented Generation (RAG) using LLaMa 3 for local contract analysis. This project demonstrates how to extract insights from unstructured data (PDF contracts) using LLMs, combining natural language processing (NLP) for intent detection and vector search.

## Overview
- **Goal:** 

    Simulate contract analysis using open-source LLMs with RAG.
- **Models Used:**
    - LLaMa 3 (for local chat without cost)
    - BERT/BART/Pegasus (for intent extraction and summarization)
- **Core Workflow:**
    1. PDF Ingestion
    2. Intent Detection
    3. Vector Database Creation
    4. RAG-Based Question Answering

This project also explores how this local implementation can be scaled using AWS Bedrock for enterprise use cases.

## Installation
1. Clone the repo:
    ```bash
    git clone https://github.com/gilvan-nascimento-filho/llm-rag-contract-analyzer.git
    cd llm-rag-contract-analyzer
    ```

2. Set up a virtual environment:
    ```bash
    python -m venv venv
    source venv/bin/activate # On Windows, use `venv\Scripts\activate`
    ```
    
3. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```
## Usage
1. **Ingest Contracts**
    
    Place PDF contracts in `data/sample/contracts/`.

2. **Generate Vector Index**
    ```bash
    python src/ingest.py
    ```

3. **Chat with the LLM**
    ```bash
    python/src/interface.py
    ````

## How It Works
1. **PDF Parsing & Intent Extraction:**

    Uses BERT/BART/Pegasus to identify the main clauses and questions.

2. **Vector Search:**

    Converts text into embeddings for RAG-based lookup.

3. **LLM Response:**

    Uses LLaMa 3 to answer questions, combining context from PDF data.

## Future Work
- Scale to AWS Bedrock for real-world deployment.
- Add evaluation metrics (accuracy, latency).
- Expand supported document types (e.g., DOCX, JSON).