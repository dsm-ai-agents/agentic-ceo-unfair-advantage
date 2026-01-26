## Lesson 3. Data Transformation Operations

This lesson focuses on **how data is shaped, controlled, and cleaned** once it enters the system.

The goal is not to cover every possible transformation node, but to build a strong intuition for **how data should be manipulated before it is stored, analyzed, or passed to an AI agent**.

---

### Objective of this Lesson

To understand the core operations required to turn raw input into **usable, reliable data**.

This lesson emphasizes precision and control over data flow.

---

### Operations covered in this lesson

#### Edit Fields  
Used to restructure data by:
- Renaming fields
- Removing unnecessary fields
- Creating new fields from existing values

This is where data is made explicit and intentional.

---

#### Filter  
Used to control which data moves forward in the workflow.

Filters act as guardrails, ensuring that only relevant records continue through the system.

---

#### Filter and Limit  
Combines logical conditions with volume control.

This operation ensures that:
- Only valid data passes through
- Data volume remains manageable

---

#### Sort  
Used to impose order on data.

Sorting is essential when:
- Prioritizing records
- Preparing data for updates
- Controlling execution logic

---

#### Remove Duplicates  
Ensures data integrity by eliminating repeated records.

This step prevents silent errors that compound over time.

---

### Why this lesson matters

AI agents do not fix bad data.

This lesson builds the habit of:
- Cleaning data early
- Making transformations visible
- Reducing ambiguity before reasoning

Clean inputs produce stable systems.

---

### Mental model to keep in mind

- Data enters messy
- n8n enforces structure
- Agents reason only after transformation

If data is unclear, stop here and fix it.

---