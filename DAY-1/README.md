# Day 1 — Groq API and Prompt-Based Assistant

This notebook introduces the Groq API and demonstrates how to build a simple prompt-controlled assistant. It was developed for the **DriveReady OPC 2026** course using Google Colab.

## Notebook Overview

The notebook covers:

- Installing `langchain_groq`
- Importing `ChatGroq`
- Connecting to the Groq API using a Colab secret
- Creating a system prompt for an assistant
- Sending user questions to the model
- Testing a prompt-injection/unsafe-action example with a guard model

## Example Use Case

The main assistant is configured for **Sweet Crumbs Home Bakery** and follows these rules:

- Custom orders require at least 24 hours of notice
- Cakes include eggless versions
- It does not promise delivery times
- It says when it does not know something
- It replies politely and in under 60 words

The notebook asks: "Can I get my order today evening?"

## Requirements

- Google Colab or a Python 3 environment
- A Groq API key
- Internet access

## Setup

1. Open `Day1.ipynb` in Google Colab.
2. Install the required package:

```bash
pip install langchain_groq
```

3. Add a Colab secret named `GROQ_API_KEY`.
4. Run the notebook cells in order.

## Key Code

### Initialize the Groq chat model

```python
from langchain_groq import ChatGroq

llm = ChatGroq(
    model="openai/gpt-oss-120b",
    temperature=0,
)
```

### Ask a question

```python
def ask(question):
    return llm.invoke([
        ("system", SYSTEM),
        ("human", question),
    ]).content

print(ask("Can I get my order today evening?"))
```

## Security Notes

The notebook demonstrates direct API-key setup through Colab secrets. Do not paste API keys into notebook source code or commit them to GitHub.

It also includes an example using the `meta-llama/llama-prompt-guard-2-22m` model to examine whether a prompt requests an unsafe action.

## File

- [`Day1.ipynb`](./Day1.ipynb)
