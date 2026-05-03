---
name: mcp-orchestration
description: 'This skill enables Agent to operate as an Active Agent rather than a passive text generator. It allows the model to interact with the Model Context Protocol (MCP), enabling it to browse files, call APIs, and execute local/remote tools to ground its prompt generation in real-world data. Use when you want to ensure that the agent can access up-to-date information and perform actions beyond text generation, such as fetching data from APIs or managing project tasks.'
---
# Skill: Model Context Protocol Orchestration (v1.0)
## Metadata
- **ID:** SKILL-MCP-ORCHESTRATION
- **Domain:** Agentic Automation / Tool Integration

## Description
This skill enables Agent to operate as an **Active Agent** rather than a passive text generator. It allows the model to interact with the Model Context Protocol (MCP), enabling it to browse files, call APIs, and execute local/remote tools to ground its prompt generation in real-world data.

## Operational Logic (P.A.O. Loop)
When a task requires data outside the current context window, Agent must execute the **Plan-Act-Observe** loop:

### 1. Plan (Tool Discovery)
- **Action:** Query the connected MCP servers (e.g., GitHub, Google Search, Slack) for available functions.
- **Decision:** Select the tool that minimizes latency while maximizing data accuracy.

### 2. Act (Standardized Execution)
- **Action:** Formulate the function call using JSON-RPC. 
- **User Transparency:** Always output a short message: `[ACTING: Querying Google Search for latest GPT-5 tokens...]` before execution.

### 3. Observe (Validation & Grounding)
- **Action:** Ingest the tool's return data.
- **Synthesis:** Integrate the results into the prompt drafting process. If the tool fails (404, 500, Timeout), attempt one alternative path before defaulting to user inquiry.

## Implementation Examples for Agent

### Scenario A: API Grounding
**User:** "Create a prompt to help me write a Slack bot using the latest Bolt API."
**Skill Execution:**
- **Plan:** Search MCP for Slack API documentation.
- **Act:** Fetch latest Bolt SDK methods.
- **Observe:** Use the actual method names in the generated prompt's example section.

### Scenario B: Project Management Handshake
**User:** "Once this prompt is finished, create a Jira ticket for it."
- **Plan:** Locate Jira MCP connector.
- **Act:** Post ticket with the generated prompt as the description.

## Guardrails
- **Read-Only Default:** Unless explicitly authorized by the user, all MCP calls should be `GET` or `READ` operations. 
- **Security:** Never transmit workspace secrets, .env files, or private keys through an MCP bridge to a third-party server.
- **Human-in-the-Loop:** High-impact actions (e.g., deleting a file, sending an email, pushing a commit) REQUIRE a `[CONFIRM]` button interaction.

## Variables Managed
- `[MCP_CONNECTION_STATUS]`
- `[ACTIVE_TOOL_NAME]`
- `[EXECUTION_RATIONALE]`
- `[TOOL_OUTPUT_DATA]`