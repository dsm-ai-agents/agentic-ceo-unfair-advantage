\# RAG (Retrieval Augmented Generation) – Basic Concept



This workflow demonstrates the \*\*foundational architecture of RAG\*\* in n8n using in-memory components.



It establishes the conceptual model before introducing production-grade persistence.



> This is where you learn \*\*what RAG is\*\*.

> 

> The MongoDB variant shows you \*\*how to deploy it\*\*.



---



\## What This Workflow Does



The pipeline consists of:



\### 1. AI Agent

Handles reasoning and decides when to retrieve knowledge



\### 2. Google Gemini Chat Model

Provides the language understanding and generation capabilities



\### 3. Simple Memory

Stores conversation history temporarily during the session



\### 4. Gemini Search Tool

Enables the agent to search for external information when needed



\### 5. Simple Vector Store

Stores and retrieves embedded knowledge using semantic similarity



\### 6. Embeddings Google Gemini

Converts text into vector representations for semantic search



The workflow demonstrates the complete RAG loop:



\*\*Input → Agent Reasoning → Retrieval (if needed) → Response\*\*



---



\## What This Workflow Is For



This workflow is designed to help you:



\- Understand the core components of RAG architecture

\- See how retrieval augments generation

\- Learn how agents decide when to use tools

\- Grasp the difference between memory and knowledge retrieval

\- Build intuition before moving to production systems



---



\## What This Workflow Does Not Cover



To maintain conceptual clarity, this workflow intentionally excludes:



\- Persistent storage (MongoDB, Pinecone, etc.)

\- Production-grade vector databases

\- Advanced retrieval strategies

\- Conversation persistence across sessions

\- Scalability and performance optimization



These are covered in the production-ready variant.



---



\## Mental Model to Keep in Mind



RAG has three distinct data flows:



1\. \*\*Conversation Memory\*\* – What was said in this chat session

2\. \*\*Knowledge Retrieval\*\* – What the agent can look up from stored documents

3\. \*\*Tool Usage\*\* – How the agent decides to use retrieval vs. other tools



Confusing these three leads to broken agent design.



---



\## Workflow Breakdown



\### The Chat Entry Point



\*\*When chat message received\*\* triggers the workflow.



This is where user input enters the system.



\#### What this demonstrates



\- How n8n workflows respond to chat interactions

\- Where the reasoning loop begins

\- How input flows into the agent



---



\### The AI Agent (Core Orchestrator)



The \*\*AI Agent\*\* node is the brain of the system.



It receives:

\- User input

\- Conversation memory

\- Available tools



It decides:

\- Whether to retrieve knowledge

\- Whether to use search

\- How to formulate a response



\#### What this demonstrates



\- Agentic reasoning vs. simple Q\&A

\- How tools expand agent capabilities

\- Why agents are more than chat models



\#### Critical insight



The agent doesn't always retrieve.

It only retrieves when retrieval would help answer the query.



This is the "augmented" in Retrieval Augmented Generation.



---



\### The Chat Model



\*\*Google Gemini Chat Model\*\* provides the language understanding.



\#### What this demonstrates



\- The agent uses a chat model for reasoning

\- The model can be swapped (Gemini, GPT, Claude, etc.)

\- The model is a component, not the system



---



\### Simple Memory



\*\*Simple Memory\*\* stores the conversation history temporarily.



This is:

\- Ephemeral (lasts only during workflow execution)

\- Conversation-specific

\- Not searchable or retrievable



\#### What this demonstrates



\- Memory ≠ Knowledge

\- Memory stores dialogue flow

\- Memory helps maintain context



\#### Key distinction



Memory is \*\*what was said\*\*.

Knowledge is \*\*what can be retrieved\*\*.



---



\### The Vector Store \& Embeddings



\*\*Simple Vector Store\*\* stores document embeddings.



\*\*Embeddings Google Gemini\*\* converts text to vectors.



Together they enable semantic retrieval.



\#### What this demonstrates



\- How text becomes searchable by meaning

\- Why embeddings are required for semantic search

\- How similarity search differs from keyword search



\#### Critical insight



The vector store doesn't store raw text in a readable form.

It stores mathematical representations that capture meaning.



Retrieval returns documents \*\*similar in meaning\*\* to the query.



---



\### The Data Ingestion Flow



The second workflow (\*\*When clicking 'Execute workflow'\*\*) shows knowledge ingestion.



It consists of:



\### 1. Edit Fields (manual)

Where you provide the raw text/documents



\### 2. Simple Vector Store1

Receives and indexes the embedded documents



\### 3. Embeddings Google Gemini

Converts raw text into vector format



\### 4. Default Data Loader

Prepares documents for embedding



\#### What this demonstrates



\- Knowledge doesn't appear magically

\- Ingestion is a separate, deliberate process

\- The quality of retrieval depends on ingestion quality



\#### Key insight



You must explicitly load knowledge before the agent can retrieve it.



RAG is not a database. It's a retrieval system.



---



\## Why This Basic Concept Matters



Most people confuse RAG with:

\- A smarter chatbot

\- A database query system

\- Automatic knowledge integration



RAG is none of these.



RAG is:

\- An architecture for combining retrieval with generation

\- A system where agents decide when to look things up

\- A pattern for augmenting LLM responses with external knowledge



This workflow strips away production concerns to show you the pure concept.



---



\## Mental Checkpoint



Before moving to production variants, you should be able to explain:



\- Why the agent doesn't always retrieve

\- The difference between memory and knowledge

\- Why embeddings are necessary

\- What happens during ingestion vs. retrieval

\- Why the vector store is separate from the chat model



If you cannot explain these, review the workflow again.



---



\## What Happens Next



This workflow is conceptual, not production-ready.



The next step is the \*\*MongoDB variant\*\*, which:

\- Externalizes memory (survives restarts)

\- Uses MongoDB Atlas for vector search

\- Makes conversations auditable

\- Enables real-world deployment



The concepts remain identical.

The architecture becomes durable.



---



\## The Core Truth About RAG



RAG doesn't make language models smarter.



RAG gives language models \*\*access to knowledge they don't have\*\*.



The difference is profound.



---



At this point, you understand:



\- What RAG is

\- How the components interact

\- Why retrieval is optional, not automatic

\- The difference between memory and knowledge



You are ready for production architecture.

