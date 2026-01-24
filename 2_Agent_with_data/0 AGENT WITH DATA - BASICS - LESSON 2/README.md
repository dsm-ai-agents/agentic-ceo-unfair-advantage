## Lesson 2. Data Capture and Ingestion

This lesson focuses on **how data enters the system**.

Before data can be transformed, analyzed, or reasoned over by an AI agent, it must be captured reliably from the outside world. This lesson establishes the entry points of the system.

---

### Objective of this Lesson

To understand how different triggers introduce data into n8n and how that data is stored for downstream processing.

This is about **ingestion discipline**, not automation complexity.

---

### What this lesson covers

- **Form Trigger**  
  Captures structured input directly from users.

- **Gmail Trigger**  
  Ingests data from incoming emails and attachments.

- **Chat Trigger**  
  Accepts conversational input that can later be routed into workflows or agents.

- **HTTP Node**  
  Allows external systems to push data into n8n programmatically.


---

### Why this lesson matters

If data enters inconsistently, everything downstream becomes unreliable.

This lesson teaches:
- Controlled entry points
- Clear ownership of incoming data
- Separation between ingestion and processing

Strong systems are built at the boundaries.

---

### Mental model to keep in mind

- Triggers define **where data comes from**
- n8n normalizes incoming data
- Storage and transformation happen later

If ingestion is unclear, debugging becomes impossible.

---