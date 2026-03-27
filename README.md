# GenAI Document Intelligence System (RAG Pipeline)

An end-to-end Retrieval-Augmented Generation (RAG) system for extracting, understanding, and querying information from PDF documents using large language models.

## Overview

This project implements a document intelligence pipeline that enables users to:

* Process PDF documents, including scanned files using OCR
* Perform semantic and keyword-based retrieval over document content
* Query documents using natural language
* Receive grounded answers with page-level citations

The system combines semantic retrieval, keyword search, and LLM-based reasoning to improve accuracy and reduce hallucinations.

## Architecture

### Pipeline Flow

1. Document Ingestion

   * PDF upload
   * OCR for scanned documents

2. Preprocessing

   * Sentence-aware semantic chunking
   * Metadata extraction (page numbers)

3. Embedding and Indexing

   * Embeddings using Sentence Transformers
   * FAISS vector database for similarity search

4. Retrieval Layer

   * Hybrid retrieval combining:

     * Dense embeddings (semantic search)
     * BM25 (keyword search)
   * Maximal Marginal Relevance (MMR) for diversity

5. LLM Reasoning

   * Query and retrieved context processed using Groq API

6. Answer Generation

   * Source-grounded responses
   * Page-level citation
   * Prompt constraints to reduce hallucinations

## Key Features

* OCR-enabled PDF processing
* Sentence-aware semantic chunking
* FAISS-based vector similarity search
* Hybrid retrieval (BM25 + embeddings)
* MMR for improved retrieval diversity
* Source-grounded responses with citations
* Modular and extensible pipeline

## Example Queries

* What is a data incident?
* Who published the guidance notes?
* Summarize the document

## Tech Stack

* Language: Python
* LLM API: Groq (LLaMA models)
* Embeddings: Sentence Transformers (`all-MiniLM-L6-v2`)
* Vector Database: FAISS
* Keyword Search: BM25
* OCR: Tesseract
* Environment: Google Colab

## Installation

```bash
pip install -r requirements.txt
```

## Usage

### 1. Upload PDF

```python
from google.colab import files
uploaded = files.upload()
```

### 2. Run Pipeline

* Extract text (with OCR fallback)
* Perform semantic chunking
* Generate embeddings
* Build FAISS index
* Initialize BM25

### 3. Query the Document

```python
ask_question("What is a data incident?")
```
## Evaluation

The system was evaluated using representative queries to assess:

* Retrieval relevance
* Answer accuracy
* Source attribution

## Key Learnings

* Sentence-aware chunking significantly improves retrieval quality compared to fixed-size chunking
* Hybrid retrieval improves recall across both semantic and keyword-based queries
* MMR reduces redundancy and improves contextual coverage
* Prompt design plays a critical role in controlling hallucinations

## Reproducibility

1. Install dependencies using `requirements.txt`
2. Add your API key in a `.env` file
3. Upload any PDF document and run the pipeline

## Future Work

* Streamlit-based user interface
* Multi-document querying
* Persistent vector database (e.g., ChromaDB)
* Automated evaluation metrics

## Author 
Adrij Ghosh
Srimoyee Bhowmick
