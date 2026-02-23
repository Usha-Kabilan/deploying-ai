# 🤖 Nova AI Assistant -- Assignment 2

## 📌 Overview

Nova AI Assistant is a conversational AI system built with a chat-based
interface using Gradio. The system integrates three backend services:

1.  API-based service (Weather API)
2.  Semantic search service using ChromaDB (persistent)
3.  A function-based calculation service

The assistant has a distinct personality, maintains short-term memory
during conversations, and includes guardrails to prevent restricted
topics and prompt manipulation.

------------------------------------------------------------------------

# Chat Client Personality

Nova is designed to be:

-   Professional\
-   Concise\
-   Friendly\
-   Insightful

This personality is implemented using a system prompt passed into the
LLM for conversational responses.

------------------------------------------------------------------------

# API Configuration

This project uses a course-provided API gateway key instead of a
personal OpenAI API key.

-   `API_GATEWAY_KEY` is used for authentication.
-   A custom `base_url` connects through the course API gateway.

All model calls and embedding requests are routed through the
institutional gateway.

------------------------------------------------------------------------

# Services Implemented

##Service 1 -- API-Based Weather Service

**Backend:** Open-Meteo Public API\
**Purpose:** Retrieve current weather conditions for Toronto.

Process: 1. User asks about weather. 2. The system calls the Open-Meteo
API. 3. JSON response is parsed. 4. Output is transformed into natural
language (not returned verbatim).

------------------------------------------------------------------------

## Service 2 -- Semantic Search (ChromaDB Persistent)

**Backend:** ChromaDB Persistent Client\
**Embedding Model:** text-embedding-3-small (via API Gateway)

### Dataset

A small knowledge base of AI-related concepts is embedded and stored: -
Artificial Intelligence - Machine Learning - Neural Networks - Deep
Learning

### Retrieval Process

1.  User question is embedded.
2.  Similar documents are retrieved.
3.  Retrieved context is passed to the LLM to generate the final
    response.
------------------------------------------------------------------------

## Service 3 -- Function-Based Calculator

This service evaluates mathematical expressions.

Example:

User: \> calculate 8 \* 7

Assistant: \> 56

------------------------------------------------------------------------

# Guardrails

The assistant blocks:

### Restricted Topics

-   Cats or dogs\
-   Taylor Swift

### Prompt Manipulation

-   Attempts to reveal the system prompt\
-   Attempts to override instructions

Guardrails are applied before routing requests to any service.

------------------------------------------------------------------------

# Memory Management

-   Conversation history is stored in memory.
-   User and assistant messages are appended to a history list.
-   A maximum history size is enforced to prevent context overflow.

------------------------------------------------------------------------

# User Interface

Implemented using Gradio: - Chatbot display - Text input - Clear
button - Real-time interaction

------------------------------------------------------------------------


