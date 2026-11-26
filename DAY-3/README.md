# Day 3 — Retrieval-Augmented Generation (RAG)

## Overview

Day 3 explores Retrieval-Augmented Generation (RAG) using a Jupyter notebook in Google Colab. The notebook demonstrates how to retrieve relevant context from documents and provide that information to a Groq-hosted language model when generating an answer.

This practical builds on the prompt engineering and chatbot concepts covered in Day 1 and Day 2.

## Objectives

- Understand the purpose of retrieval-augmented generation
- Create embeddings for text documents
- Store and search document vectors
- Retrieve relevant context for a user question
- Generate responses using retrieved context and an LLM
- Compare responses with and without retrieved context

## Technologies Used

- Python
- Google Colab
- Jupyter Notebook
- Groq API
- LangChain
- Vector embeddings
- Vector database or in-memory vector store

## Notebook Workflow

```mermaid
flowchart LR
    A[Source Documents] --> B[Text Splitting]
    B --> C[Embeddings]
    C --> D[Vector Store]
    E[User Question] --> F[Similarity Search]
    D --> F
    F --> G[Relevant Context]
    G --> H[Prompt + Question]
    E --> H
    H --> I[Groq LLM]
    I --> J[Grounded Response]
```

## Prerequisites

- A Google account
- Google Colab access
- A Groq API key
- Internet access

## How to Run

1. Open [`Day3.ipynb`](./Day3.ipynb) in Google Colab.
2. Install the dependencies requested in the notebook:

```bash
pip install -q langchain langchain-groq langchain-community faiss-cpu
```

3. Add a Colab secret named `GROQ_API_KEY`.
4. Run the notebook cells in sequence.
5. Change the sample question or source text to test the RAG pipeline.

## File

- [`Day3.ipynb`](./Day3.ipynb) — implementation notebook for Day 3

## Security

Do not paste the Groq API key directly into a notebook cell or commit secrets to GitHub. Use Google Colab Secrets and read the key as shown in the notebook.

## Learning Outcomes

After completing Day 3, you should understand:

- How RAG reduces unsupported or hallucinated answers
- How document chunking affects retrieval quality
- How embeddings represent text for semantic search
- How retrieved context is injected into an LLM prompt
- How to build a basic question-answering pipeline using external knowledge