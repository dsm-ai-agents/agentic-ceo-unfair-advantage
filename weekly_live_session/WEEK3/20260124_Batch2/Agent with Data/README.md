# \# CRM Agent

# 

# This workflow creates an \*\*AI-powered CRM agent\*\* that manages lead data in Google Sheets through natural conversation.

# 

# It demonstrates how AI agents can interact with structured data systems using natural language commands.

# 

# ---

# 

# \## What This Workflow Does

# 

# The pipeline consists of:

# 

# \### 1. Chat Trigger

# Receives natural language commands from users

# 

# \### 2. CRM Agent

# Interprets requests and orchestrates Google Sheets operations

# 

# \### 3. Google Gemini Chat Model

# Provides language understanding and reasoning capabilities

# 

# \### 4. Simple Memory

# Maintains conversation context for follow-up commands

# 

# \### 5. Leads Database (read: sheet)

# Reads lead data to understand structure and current state

# 

# \### 6. Add Lead (append: sheet)

# Creates new lead records in the database

# 

# \### 7. Delete Lead (delete: sheet)

# Removes lead records from the database

# 

# \### 8. Update Lead (update: sheet)

# Modifies existing lead information

# 

# The complete flow:

# 

# \*\*Natural Language → Agent Reasoning → Database Operation → Confirmation\*\*

# 

# ---

# 

# \## System Prompt Configuration

# 

# The agent operates with specific instructions:

# 

# ```

# You are a CRM Agent. Use the google sheets tool to create a row 

# when prompted by the user. Always get rows first to understand 

# the column names in the sheet and then as per the user's request, 

# create or update the row or rows.

# ```

# 

# \### Key Behaviors

# 

# \*\*Always reads first\*\*: The agent checks the sheet structure before making changes

# 

# \*\*Context-aware operations\*\*: Understands column names and data format from the existing sheet

# 

# \*\*Flexible execution\*\*: Handles create, update, and delete operations based on user intent

# 

# ---

# 

# \## What This Workflow Is For

# 

# This workflow helps you:

# 

# \- Manage CRM data using natural language instead of manual entry

# \- Build conversational interfaces for database operations

# \- Create agents that understand structured data contexts

# \- Demonstrate CRUD operations through AI orchestration

# 

# ---

# 

# \## How It Works

# 

# \### Step 1: User Request

# 

# A user sends a natural language command:

# \- "Add a new lead named John Doe with email john@example.com"

# \- "Update Sarah's phone number to 555-0123"

# \- "Delete the lead for ABC Corp"

# 

# \### Step 2: Agent Processing

# 

# The \*\*CRM Agent\*\*:

# 1\. Reads the Leads Database to understand column structure

# 2\. Interprets the user's intent

# 3\. Maps natural language to the appropriate tool

# 4\. Determines which fields to modify

# 

# \### Step 3: Database Operation

# 

# Based on intent, the agent uses:

# \- \*\*Add Lead\*\* for new entries

# \- \*\*Update Lead\*\* for modifications

# \- \*\*Delete Lead\*\* for removals

# 

# \### Step 4: Confirmation

# 

# The agent confirms the action taken and reports success or issues.

# 

# ---

# 

# \## Example Interactions

# 

# \### Adding a Lead

# ```

# User: Add a lead for Jane Smith, email jane@startup.io, 

# &nbsp;     company StartupCo

# Agent: \[Reads sheet structure]

# &nbsp;      \[Creates new row with provided data]

# &nbsp;      "I've added Jane Smith to the leads database."

# ```

# 

# \### Updating a Lead

# ```

# User: Change John's status to 'qualified'

# Agent: \[Reads current data]

# &nbsp;      \[Updates John's status field]

# &nbsp;      "Updated John's status to qualified."

# ```

# 

# \### Deleting a Lead

# ```

# User: Remove the lead for Acme Corp

# Agent: \[Finds matching record]

# &nbsp;      \[Deletes the row]

# &nbsp;      "Deleted the lead for Acme Corp."

# ```

# 

# ---

# 

# \## Critical Design Pattern

# 

# \### Why "Read First"?

# 

# The agent \*\*always reads the sheet first\*\* because:

# 

# 1\. \*\*Schema Discovery\*\*: Column names and structure may vary

# 2\. \*\*Data Validation\*\*: Understanding existing data prevents errors

# 3\. \*\*Context Awareness\*\*: Can reference existing leads by name or company

# 4\. \*\*Smart Updates\*\*: Knows which fields exist and which to modify

# 

# This pattern makes the agent adaptable to different sheet structures without hardcoding field names.

# 

# 

# ---

# 

# \## Mental Model

# 

# This is not a form interface.

# 

# This is a \*\*conversational database operator\*\*.

# 

# The difference:

# \- Forms require structured input

# \- Agents interpret natural language

# \- Forms lock you into fields

# \- Agents adapt to intent

# 

# The agent bridges human communication and structured data.

# 

# ---

# 

# \## Use Cases

# 

# This workflow pattern enables:

# 

# \- Chat-based lead management for remote workers

# \- Quick updates without opening spreadsheets

# \- Non-technical users managing databases

# \- Rapid prototyping of data entry automation

# 

# ---

# 

# \## The Core Insight

# 

# Spreadsheets are interfaces for humans who think in grids.

# 

# Agents are interfaces for humans who think in sentences.

# 

# This workflow translates between the two.

# 

# ---

# 

