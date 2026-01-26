# CRM Agent

## Workflow Overview

This workflow creates an AI-powered CRM agent that manages lead data in Google Sheets through natural conversation.

It demonstrates how AI agents can interact with structured data systems using natural language commands.

---

## Workflow Diagram

```
Chat Trigger → CRM Agent → [Tools: Model, Memory, Google Sheets CRUD] → Confirmation
```

---

## Node Sequence

1. **Chat Trigger** - Receives natural language commands from users
2. **CRM Agent** - Interprets requests and orchestrates Google Sheets operations
   - **Google Gemini Chat Model** - Provides language understanding and reasoning
   - **Simple Memory** - Maintains conversation context for follow-up commands
   - **Leads Database (read: sheet)** - Reads lead data to understand structure
   - **Add Lead (append: sheet)** - Creates new lead records
   - **Delete Lead (delete: sheet)** - Removes lead records
   - **Update Lead (update: sheet)** - Modifies existing lead information

---

## System Prompt

Copy and paste this into your AI Agent node:

```
You are a CRM Agent. Use the google sheets tool to create a row
when prompted by the user. Always get rows first to understand
the column names in the sheet and then as per the user's request,
create or update the row or rows.
```

**Key Behaviors:**
- **Always reads first** - Checks sheet structure before making changes
- **Context-aware operations** - Understands column names and data format
- **Flexible execution** - Handles create, update, and delete based on user intent

---

## What This Workflow Does

- Manages CRM data using natural language instead of manual entry
- Interprets user intent and maps to appropriate database operations
- Reads sheet structure dynamically to understand data schema
- Performs CRUD operations (Create, Read, Update, Delete) on lead data
- Confirms actions and reports success or issues

---

## How It Works

**Step 1: User Request**

A user sends a natural language command:
- "Add a new lead named John Doe with email john@example.com"
- "Update Sarah's phone number to 555-0123"
- "Delete the lead for ABC Corp"

**Step 2: Agent Processing**

The CRM Agent:
1. Reads the Leads Database to understand column structure
2. Interprets the user's intent
3. Maps natural language to the appropriate tool
4. Determines which fields to modify

**Step 3: Database Operation**

Based on intent, the agent uses:
- **Add Lead** for new entries
- **Update Lead** for modifications
- **Delete Lead** for removals

**Step 4: Confirmation**

The agent confirms the action taken and reports success or issues.

---

## Example Interactions

**Adding a Lead:**
```
User: Add a lead for Jane Smith, email jane@startup.io, company StartupCo
Agent: [Reads sheet structure]
       [Creates new row with provided data]
       "I've added Jane Smith to the leads database."
```

**Updating a Lead:**
```
User: Change John's status to 'qualified'
Agent: [Reads current data]
       [Updates John's status field]
       "Updated John's status to qualified."
```

**Deleting a Lead:**
```
User: Remove the lead for Acme Corp
Agent: [Finds matching record]
       [Deletes the row]
       "Deleted the lead for Acme Corp."
```

---

## Critical Design Pattern

**Why "Read First"?**

The agent always reads the sheet first because:

1. **Schema Discovery** - Column names and structure may vary
2. **Data Validation** - Understanding existing data prevents errors
3. **Context Awareness** - Can reference existing leads by name or company
4. **Smart Updates** - Knows which fields exist and which to modify

This pattern makes the agent adaptable to different sheet structures without hardcoding field names.

---

## Use Cases

- Voice-controlled CRM entry for sales teams
- Chat-based lead management for remote workers
- Quick updates without opening spreadsheets
- Non-technical users managing databases
- Rapid prototyping of data entry automation

---

## Limitations

**Memory is Ephemeral**
- Conversation context only persists during the session
- For production, use persistent memory like MongoDB

**Sheet Structure Assumptions**
- Works best with well-structured sheets
- Messy or inconsistent data may confuse the agent

**No Complex Queries**
- Handles simple CRUD operations only
- Not suitable for advanced filtering or analytics

---

## Production Considerations

To make this production-ready:

1. **Add data validation** to prevent malformed entries
2. **Implement error handling** for sheet access and operation failures
3. **Use MongoDB or real CRM** instead of Google Sheets for scalability
4. **Add user authentication** to track who makes changes
5. **Include audit logging** for compliance and debugging
6. **Handle edge cases** like duplicate detection and conflict resolution

---

## Mental Model

This is not a form interface.

**This is a conversational database operator.**

The difference:
- Forms require structured input → Agents interpret natural language
- Forms lock you into fields → Agents adapt to intent
- Forms need training → Agents understand context

The agent bridges human communication and structured data.

---

## Architecture Pattern

```
Natural Language → Intent Recognition → Schema Discovery → Database Operation → Confirmation
```

The agent translates sentences into structured database operations by first understanding the data context.

---

## The Core Insight

Spreadsheets are interfaces for humans who think in grids.

Agents are interfaces for humans who think in sentences.

This workflow translates between the two.

---

## Why This Matters

Most business data lives in spreadsheets.

Most business conversations happen in natural language.

Agents that bridge these worlds eliminate friction and enable non-technical users to manage data effectively.
