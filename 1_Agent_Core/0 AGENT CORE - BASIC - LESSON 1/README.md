## RAG (Retrieval Augmented Generation)



This section introduces \*\*Retrieval Augmented Generation (RAG)\*\* using simple and incremental n8n workflows.



The goal here is not to build a production-ready RAG system. The goal is to build \*\*conceptual clarity\*\*. Every workflow is designed to explain one idea at a time so students understand \*why\* each component exists before worrying about scale or optimization.



By the end of this section, students should clearly understand:

\- Why large language models need external knowledge sources

\- How embeddings convert unstructured data into searchable representations

\- How vector stores enable semantic retrieval

\- How retrieved context is injected into an agent’s reasoning loop



---



\### What this section covers



\- Creating embeddings from raw data

\- Storing embeddings in a vector store

\- Retrieving relevant context based on user queries

\- Feeding retrieved context into an AI agent for grounded responses



Each workflow follows a \*\*single-responsibility principle\*\*. One trigger, one core transformation, and one storage or retrieval action. This keeps the learning curve linear and intentional.



---



\### What this section does not cover



\- Advanced chunking strategies

\- Large-scale or distributed vector databases

\- Hybrid search, reranking, or multi-vector retrieval

\- Cost optimization, caching, or performance tuning



Those topics are important but intentionally excluded at this stage. Introducing them early would reduce understanding rather than improve it.



---



\### How to use these workflows



Students are expected to:

\- Run workflows manually

\- Change inputs and observe different retrieval results

\- Inspect embeddings and vector store behavior

\- Break workflows intentionally to understand failure modes



If you cannot explain \*\*why a node exists\*\*, you are moving too fast.



---



\### Mental model to keep in mind



RAG is not a feature.  

RAG is a \*\*feedback loop\*\*.



1\. Knowledge is stored externally

2\. User intent is embedded

3\. Relevant context is retrieved

4\. The agent reasons with grounded information



Every workflow in this section exists to make that loop obvious.



---



\### Workflow 1. Creating the First AI Agent



This workflow introduces the \*\*most fundamental building block\*\* of the entire Agentic CEO program. A basic AI agent that can receive a message, reason over it, and respond.



There is no retrieval, no memory, and no tools involved yet. Thiscmplicity is intentional.



The purpose of this workflow is to help students understand \*\*what an AI agent actually is\*\* before adding intelligence layers on top.



---



\#### What this workflow demonstrates



\- How an AI agent is triggered by a chat message

\- How a chat model is attached to an agent

\- How input flows from the trigger into the agent

\- How the agent generates a response using the model



This workflow establishes the \*\*baseline behavior\*\* of an agent. Everything that comes later builds on this exact structure.



---



\#### Key components explained



\- \*\*When Chat Message Received\*\*  

&nbsp; This node acts as the entry point. It listens for user input and initiates the agent’s execution cycle.



\- \*\*AI Agent\*\*  

&nbsp; This node represents the reasoning entity. At this stage, it has no memory and no tools. It only knows how to think and respond using a language model.



\- \*\*Google Gemini Chat Model\*\*  

&nbsp; This is the reasoning engine behind the agent. The model processes the input and generates a response based purely on its training and the prompt context.



---



\#### Why this workflow matters



Many learners jump straight into complex agent systems without understanding the core loop:

Input → Reasoning → Output



This workflow forces clarity.



If you do not fully understand this workflow, adding memory, tools, or retrieval will only create confusion later.



---



\#### Mental checkpoint for students



Before moving forward, you should be able to answer:

\- What triggers the agent?

\- Where does reasoning happen?

\- What role does the model play?

\- What is missing from this agent and why?



If any of these are unclear, stop here and revisit this workflow.



---



Next workflows will extend this agent with \*\*memory\*\*, without changing this core structure.



---



\### Workflow 2. Adding Memory to the AI Agent



This workflow extends the basic AI agent by introducing \*\*memory\*\*.



The agent can now retain context across messages instead of treating every interaction as an isolated event. This is the first step toward making the agent feel persistent and state-aware.



No retrieval or external knowledge is involved yet. The focus here is \*\*conversation continuity\*\*, not intelligence depth.



---



\#### What this workflow demonstrates



\- How memory is attached to an AI agent

\- How past interactions influence future responses

\- The difference between stateless and stateful agents

\- How memory changes the behavior of the same model



This workflow shows that intelligence is not just about the model. \*\*State matters.\*\*



---



\#### Key components explained



\- \*\*When Chat Message Received\*\*  

&nbsp; The trigger remains unchanged. User input still initiates the execution cycle.



\- \*\*AI Agent\*\*  

&nbsp; The agent now has an additional capability. It can store and recall past messages within a session.



\- \*\*Google Gemini Chat Model\*\*  

&nbsp; The reasoning engine remains the same. This is intentional to show that improved behavior can come from architecture, not model upgrades.



\- \*\*Simple Memory\*\*  

&nbsp; This node stores conversation history and feeds it back into the agent on each turn. It allows the agent to maintain continuity, remember prior questions, and respond more coherently over time.



---



\#### Why this workflow matters



Many people assume memory is automatic in AI systems. It is not.



This workflow makes memory explicit and shows:

\- Where memory lives

\- How it is connected

\- How it influences reasoning



Understanding this prevents confusion when building multi-turn agents later.



---



\#### Mental checkpoint for students



Before moving forward, you should be able to explain:

\- What changes when memory is added

\- What the agent remembers and what it does not

\- Why memory alone is not enough for factual grounding



If you think memory equals knowledge, you are misunderstanding the system.



---



The next workflows will introduce \*\*external knowledge via embeddings and vector stores\*\*, solving the limitations exposed here.



---



\### Workflow 3. Introducing Vector Store Based Retrieval



This workflow marks the transition from a conversational agent to a \*\*knowledge-aware agent\*\*.



For the first time, the agent is no longer limited to its training data or short-term conversation memory. It can now \*\*retrieve relevant information from an external knowledge base\*\* using embeddings.



This is the foundational step of Retrieval Augmented Generation.



---



\#### What this workflow demonstrates



\- How embeddings are generated from user input

\- How a vector store is connected as a tool to the agent

\- How semantic similarity enables retrieval

\- The difference between memory and knowledge



This workflow introduces retrieval without adding complexity elsewhere. The agent structure remains familiar on purpose.



---



\#### Key components explained



\- \*\*When Chat Message Received\*\*  

&nbsp; The trigger remains unchanged. User input still initiates the reasoning cycle.



\- \*\*AI Agent\*\*  

&nbsp; The agent now has access to memory and an external tool. This changes how it reasons, not how it is triggered.



\- \*\*Google Gemini Chat Model\*\*  

&nbsp; The model continues to handle reasoning and response generation. No model upgrade is required to add retrieval capability.



\- \*\*Simple Memory\*\*  

&nbsp; Memory maintains conversational context. It does not store factual knowledge.



\- \*\*Embeddings (Google Gemini)\*\*  

&nbsp; This node converts text into vector representations that can be compared semantically.



\- \*\*Simple Vector Store\*\*  

&nbsp; This is the agent’s external knowledge interface. It stores embeddings and returns relevant context based on similarity search.



---



\#### Why this workflow matters



This workflow exposes a critical distinction:

\- Memory remembers conversations

\- Vector stores retrieve knowledge



Conflating the two leads to broken agent designs.



This is the first point where the agent can answer questions using \*\*information it was never trained on\*\*, as long as that information exists in the vector store.



---



\#### Mental checkpoint for students



Before moving forward, you should be able to explain:

\- Why embeddings are required

\- What the vector store actually returns

\- Why memory alone cannot solve knowledge retrieval

\- How the agent decides when to use a tool



If retrieval feels magical, you have skipped a step.



---



The next workflow will focus on \*\*how data enters the vector store\*\*, completing the RAG loop.





---





\### Workflow 4. Populating the Vector Store with Text Data



This workflow completes the core RAG loop by showing \*\*how knowledge enters the vector store\*\*.



Instead of relying on external files or services, this workflow allows text to be manually entered and embedded directly. The focus here is on understanding the \*\*data ingestion step\*\* of RAG, not automation or scale.



---



\#### What this workflow demonstrates



\- How raw text is prepared for embedding

\- How embeddings are generated from custom text

\- How documents are stored inside a vector store

\- How the vector store becomes queryable by an agent later



This workflow exists purely to make the ingestion step explicit and visible.



---



\#### Key components explained



\- \*\*When Clicking “Execute Workflow”\*\*  

&nbsp; This manual trigger is used to run the workflow intentionally. It reinforces that data ingestion is a deliberate action, not something that happens automatically during chat.



\- \*\*Edit Fields\*\*  

&nbsp; This node provides a controlled space to enter one or more paragraphs of text. Whatever is written here becomes the knowledge that will later be retrieved by the agent.



\- \*\*Embeddings (Google Gemini)\*\*  

&nbsp; The text entered is converted into vector representations. These vectors capture semantic meaning, not keywords.



\- \*\*Default Data Loader\*\*  

&nbsp; This node structures the raw text into a document format suitable for embedding and storage.



\- \*\*Simple Vector Store\*\*  

&nbsp; The final destination. The embedded document is stored and becomes part of the agent’s retrievable knowledge base.



---



\#### Why this workflow matters



Retrieval systems fail most often at the ingestion layer.



This workflow makes it clear that:

\- The quality of retrieval depends on the quality of stored text

\- Embeddings are created before retrieval ever happens

\- Vector stores do not understand text. They understand vectors



Once this step is understood, all future ingestion methods follow the same pattern.



---



\#### Mental checkpoint for students



Before moving forward, you should be able to explain:

\- What text is being stored

\- How that text is transformed

\- Where the knowledge lives after execution

\- Why ingestion and retrieval are separate workflows



If you cannot trace the journey of a paragraph from input to storage, stop here.


---


At this point, the \*\*end-to-end RAG loop is complete\*\*:

\- One workflow ingests knowledge

\- Another workflow retrieves it

\- The agent reasons using grounded context



---


### Workflow 5. Extending the Agent with Internet Research Capability

This workflow adds the final capability to the RAG-based agent. The ability to **research the internet in real time**.

At this stage, the agent is no longer limited to:
- Its training data
- Conversation memory
- Pre-ingested vector knowledge

It can now decide when to fetch **fresh, external information**.

---

#### What this workflow demonstrates

- How multiple tools can coexist within a single agent
- How an agent chooses between retrieval and search
- How live internet data complements stored knowledge
- How agent capability increases through tool composition

This workflow shows that agents become powerful not by being smarter, but by being **better equipped**.

---

#### Key components explained

- **When Chat Message Received**  
  The trigger remains unchanged. User input initiates reasoning.

- **AI Agent**  
  The agent now has access to memory, a vector store, and an external search tool. This expands its action space.

- **Google Gemini Chat Model**  
  The model continues to handle reasoning and decision-making, including deciding when to invoke tools.

- **Simple Memory**  
  Maintains conversational continuity and user context.

- **Simple Vector Store**  
  Provides retrieval from previously ingested, structured knowledge.

- **Gemini Search Tool**  
  Enables real-time web research. This tool is used when the answer cannot be reliably found in memory or the vector store.

- **Embeddings (Google Gemini)**  
  Supports semantic retrieval from the vector store as before.

---

#### Why this workflow matters

This is the first time the agent can:
- Access **fresh information**
- Validate or expand on stored knowledge
- Handle questions that change over time

It introduces a critical architectural idea.  
**Different questions require different tools.**

---

#### Mental checkpoint for students

Before moving forward, you should be able to explain:
- When the agent should use vector retrieval
- When the agent should use internet search
- Why mixing both improves reliability
- Why tools do not replace reasoning

If the agent feels omniscient, something is wrong.

---

At this point, the agent has:
- Memory for continuity
- A vector store for grounded knowledge
- Internet search for freshness

This is a complete, practical RAG-based agent architecture.
## RAG (Retrieval Augmented Generation)



This section introduces \*\*Retrieval Augmented Generation (RAG)\*\* using simple and incremental n8n workflows.



The goal here is not to build a production-ready RAG system. The goal is to build \*\*conceptual clarity\*\*. Every workflow is designed to explain one idea at a time so students understand \*why\* each component exists before worrying about scale or optimization.



By the end of this section, students should clearly understand:

\- Why large language models need external knowledge sources

\- How embeddings convert unstructured data into searchable representations

\- How vector stores enable semantic retrieval

\- How retrieved context is injected into an agent’s reasoning loop



---



\### What this section covers



\- Creating embeddings from raw data

\- Storing embeddings in a vector store

\- Retrieving relevant context based on user queries

\- Feeding retrieved context into an AI agent for grounded responses



Each workflow follows a \*\*single-responsibility principle\*\*. One trigger, one core transformation, and one storage or retrieval action. This keeps the learning curve linear and intentional.



---



\### What this section does not cover



\- Advanced chunking strategies

\- Large-scale or distributed vector databases

\- Hybrid search, reranking, or multi-vector retrieval

\- Cost optimization, caching, or performance tuning



Those topics are important but intentionally excluded at this stage. Introducing them early would reduce understanding rather than improve it.



---



\### How to use these workflows



Students are expected to:

\- Run workflows manually

\- Change inputs and observe different retrieval results

\- Inspect embeddings and vector store behavior

\- Break workflows intentionally to understand failure modes



If you cannot explain \*\*why a node exists\*\*, you are moving too fast.



---



\### Mental model to keep in mind



RAG is not a feature.  

RAG is a \*\*feedback loop\*\*.



1\. Knowledge is stored externally

2\. User intent is embedded

3\. Relevant context is retrieved

4\. The agent reasons with grounded information



Every workflow in this section exists to make that loop obvious.



---



\### Workflow 1. Creating the First AI Agent



This workflow introduces the \*\*most fundamental building block\*\* of the entire Agentic CEO program. A basic AI agent that can receive a message, reason over it, and respond.



There is no retrieval, no memory, and no tools involved yet. Thiscmplicity is intentional.



The purpose of this workflow is to help students understand \*\*what an AI agent actually is\*\* before adding intelligence layers on top.



---



\#### What this workflow demonstrates



\- How an AI agent is triggered by a chat message

\- How a chat model is attached to an agent

\- How input flows from the trigger into the agent

\- How the agent generates a response using the model



This workflow establishes the \*\*baseline behavior\*\* of an agent. Everything that comes later builds on this exact structure.



---



\#### Key components explained



\- \*\*When Chat Message Received\*\*  

&nbsp; This node acts as the entry point. It listens for user input and initiates the agent’s execution cycle.



\- \*\*AI Agent\*\*  

&nbsp; This node represents the reasoning entity. At this stage, it has no memory and no tools. It only knows how to think and respond using a language model.



\- \*\*Google Gemini Chat Model\*\*  

&nbsp; This is the reasoning engine behind the agent. The model processes the input and generates a response based purely on its training and the prompt context.



---



\#### Why this workflow matters



Many learners jump straight into complex agent systems without understanding the core loop:

Input → Reasoning → Output



This workflow forces clarity.



If you do not fully understand this workflow, adding memory, tools, or retrieval will only create confusion later.



---



\#### Mental checkpoint for students



Before moving forward, you should be able to answer:

\- What triggers the agent?

\- Where does reasoning happen?

\- What role does the model play?

\- What is missing from this agent and why?



If any of these are unclear, stop here and revisit this workflow.



---



Next workflows will extend this agent with \*\*memory\*\*, without changing this core structure.



---



\### Workflow 2. Adding Memory to the AI Agent



This workflow extends the basic AI agent by introducing \*\*memory\*\*.



The agent can now retain context across messages instead of treating every interaction as an isolated event. This is the first step toward making the agent feel persistent and state-aware.



No retrieval or external knowledge is involved yet. The focus here is \*\*conversation continuity\*\*, not intelligence depth.



---



\#### What this workflow demonstrates



\- How memory is attached to an AI agent

\- How past interactions influence future responses

\- The difference between stateless and stateful agents

\- How memory changes the behavior of the same model



This workflow shows that intelligence is not just about the model. \*\*State matters.\*\*



---



\#### Key components explained



\- \*\*When Chat Message Received\*\*  

&nbsp; The trigger remains unchanged. User input still initiates the execution cycle.



\- \*\*AI Agent\*\*  

&nbsp; The agent now has an additional capability. It can store and recall past messages within a session.



\- \*\*Google Gemini Chat Model\*\*  

&nbsp; The reasoning engine remains the same. This is intentional to show that improved behavior can come from architecture, not model upgrades.



\- \*\*Simple Memory\*\*  

&nbsp; This node stores conversation history and feeds it back into the agent on each turn. It allows the agent to maintain continuity, remember prior questions, and respond more coherently over time.



---



\#### Why this workflow matters



Many people assume memory is automatic in AI systems. It is not.



This workflow makes memory explicit and shows:

\- Where memory lives

\- How it is connected

\- How it influences reasoning



Understanding this prevents confusion when building multi-turn agents later.



---



\#### Mental checkpoint for students



Before moving forward, you should be able to explain:

\- What changes when memory is added

\- What the agent remembers and what it does not

\- Why memory alone is not enough for factual grounding



If you think memory equals knowledge, you are misunderstanding the system.



---



The next workflows will introduce \*\*external knowledge via embeddings and vector stores\*\*, solving the limitations exposed here.



---



\### Workflow 3. Introducing Vector Store Based Retrieval



This workflow marks the transition from a conversational agent to a \*\*knowledge-aware agent\*\*.



For the first time, the agent is no longer limited to its training data or short-term conversation memory. It can now \*\*retrieve relevant information from an external knowledge base\*\* using embeddings.



This is the foundational step of Retrieval Augmented Generation.



---



\#### What this workflow demonstrates



\- How embeddings are generated from user input

\- How a vector store is connected as a tool to the agent

\- How semantic similarity enables retrieval

\- The difference between memory and knowledge



This workflow introduces retrieval without adding complexity elsewhere. The agent structure remains familiar on purpose.



---



\#### Key components explained



\- \*\*When Chat Message Received\*\*  

&nbsp; The trigger remains unchanged. User input still initiates the reasoning cycle.



\- \*\*AI Agent\*\*  

&nbsp; The agent now has access to memory and an external tool. This changes how it reasons, not how it is triggered.



\- \*\*Google Gemini Chat Model\*\*  

&nbsp; The model continues to handle reasoning and response generation. No model upgrade is required to add retrieval capability.



\- \*\*Simple Memory\*\*  

&nbsp; Memory maintains conversational context. It does not store factual knowledge.



\- \*\*Embeddings (Google Gemini)\*\*  

&nbsp; This node converts text into vector representations that can be compared semantically.



\- \*\*Simple Vector Store\*\*  

&nbsp; This is the agent’s external knowledge interface. It stores embeddings and returns relevant context based on similarity search.



---



\#### Why this workflow matters



This workflow exposes a critical distinction:

\- Memory remembers conversations

\- Vector stores retrieve knowledge



Conflating the two leads to broken agent designs.



This is the first point where the agent can answer questions using \*\*information it was never trained on\*\*, as long as that information exists in the vector store.



---



\#### Mental checkpoint for students



Before moving forward, you should be able to explain:

\- Why embeddings are required

\- What the vector store actually returns

\- Why memory alone cannot solve knowledge retrieval

\- How the agent decides when to use a tool



If retrieval feels magical, you have skipped a step.



---



The next workflow will focus on \*\*how data enters the vector store\*\*, completing the RAG loop.





---





\### Workflow 4. Populating the Vector Store with Text Data



This workflow completes the core RAG loop by showing \*\*how knowledge enters the vector store\*\*.



Instead of relying on external files or services, this workflow allows text to be manually entered and embedded directly. The focus here is on understanding the \*\*data ingestion step\*\* of RAG, not automation or scale.



---



\#### What this workflow demonstrates



\- How raw text is prepared for embedding

\- How embeddings are generated from custom text

\- How documents are stored inside a vector store

\- How the vector store becomes queryable by an agent later



This workflow exists purely to make the ingestion step explicit and visible.



---



\#### Key components explained



\- \*\*When Clicking “Execute Workflow”\*\*  

&nbsp; This manual trigger is used to run the workflow intentionally. It reinforces that data ingestion is a deliberate action, not something that happens automatically during chat.



\- \*\*Edit Fields\*\*  

&nbsp; This node provides a controlled space to enter one or more paragraphs of text. Whatever is written here becomes the knowledge that will later be retrieved by the agent.



\- \*\*Embeddings (Google Gemini)\*\*  

&nbsp; The text entered is converted into vector representations. These vectors capture semantic meaning, not keywords.



\- \*\*Default Data Loader\*\*  

&nbsp; This node structures the raw text into a document format suitable for embedding and storage.



\- \*\*Simple Vector Store\*\*  

&nbsp; The final destination. The embedded document is stored and becomes part of the agent’s retrievable knowledge base.



---



\#### Why this workflow matters



Retrieval systems fail most often at the ingestion layer.



This workflow makes it clear that:

\- The quality of retrieval depends on the quality of stored text

\- Embeddings are created before retrieval ever happens

\- Vector stores do not understand text. They understand vectors



Once this step is understood, all future ingestion methods follow the same pattern.



---



\#### Mental checkpoint for students



Before moving forward, you should be able to explain:

\- What text is being stored

\- How that text is transformed

\- Where the knowledge lives after execution

\- Why ingestion and retrieval are separate workflows



If you cannot trace the journey of a paragraph from input to storage, stop here.


---


At this point, the \*\*end-to-end RAG loop is complete\*\*:

\- One workflow ingests knowledge

\- Another workflow retrieves it

\- The agent reasons using grounded context



---


### Workflow 5. Extending the Agent with Internet Research Capability

This workflow adds the final capability to the RAG-based agent. The ability to **research the internet in real time**.

At this stage, the agent is no longer limited to:
- Its training data
- Conversation memory
- Pre-ingested vector knowledge

It can now decide when to fetch **fresh, external information**.

---

#### What this workflow demonstrates

- How multiple tools can coexist within a single agent
- How an agent chooses between retrieval and search
- How live internet data complements stored knowledge
- How agent capability increases through tool composition

This workflow shows that agents become powerful not by being smarter, but by being **better equipped**.

---

#### Key components explained

- **When Chat Message Received**  
  The trigger remains unchanged. User input initiates reasoning.

- **AI Agent**  
  The agent now has access to memory, a vector store, and an external search tool. This expands its action space.

- **Google Gemini Chat Model**  
  The model continues to handle reasoning and decision-making, including deciding when to invoke tools.

- **Simple Memory**  
  Maintains conversational continuity and user context.

- **Simple Vector Store**  
  Provides retrieval from previously ingested, structured knowledge.

- **Gemini Search Tool**  
  Enables real-time web research. This tool is used when the answer cannot be reliably found in memory or the vector store.

- **Embeddings (Google Gemini)**  
  Supports semantic retrieval from the vector store as before.

---

#### Why this workflow matters

This is the first time the agent can:
- Access **fresh information**
- Validate or expand on stored knowledge
- Handle questions that change over time

It introduces a critical architectural idea.  
**Different questions require different tools.**

---

#### Mental checkpoint for students

Before moving forward, you should be able to explain:
- When the agent should use vector retrieval
- When the agent should use internet search
- Why mixing both improves reliability
- Why tools do not replace reasoning

If the agent feels omniscient, something is wrong.

---

At this point, the agent has:
- Memory for continuity
- A vector store for grounded knowledge
- Internet search for freshness

This is a complete, practical RAG-based agent architecture.
---
