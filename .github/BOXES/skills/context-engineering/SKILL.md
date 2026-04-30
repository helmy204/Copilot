---
name: context-engineering
description: 'This skill enables the agent to perform "High-Precision Filtering" of conversation history. It distinguishes between transient "noise" (user small talk, irrelevant updates) and "Permanent Constraints" (brand rules, technical limitations, negative constraints). Use when you want to ensure that the agent focuses on relevant information and adheres to established guidelines throughout a session.'
---
# Skill: Context Engineering & Memory Management (v1.0)
## Metadata
- **ID:** SKILL-CONTEXT-001
- **Domain:** Prompt Engineering / Meta-Orchestration
- **Agent:** Prompt Architect Agent
- **Platform:** GitHub Copilot / VS Code / Microsoft 365

## Description
This skill enables the agent to perform "High-Precision Filtering" of conversation history. It distinguishes between transient "noise" (user small talk, irrelevant updates) and "Permanent Constraints" (brand rules, technical limitations, negative constraints).

## Operational Logic (C.E.M.M.)
When this skill is activated, Agent must execute the following "Thinking Loop":

### 1. The Noise Filter
- **Action:** Scan the last 10 messages for irrelevant context.
- **Rule:** If the user discusses non-task-related topics (e.g., weather, lunch, greetings), flag these as `volatile_memory` and exclude them from the prompt synthesis phase.

### 2. Constraint Locking
- **Action:** Identify "Hard Rules" provided by the user.
- **Syntax Recognition:** Automatically capture phrases like "Never use...", "Always include...", and "Target audience is...".
- **Storage:** Maintain these in a `Active_Context_Block` that persists even if the chat history grows long.

### 3. Semantic Retrieval (2026 Standard)
- **Action:** If the user references a past project or successful prompt, perform a semantic search.
- **Heuristic:** "Does this new request share a 70%+ similarity with Project X?" If yes, suggest importing Project X's `Negative_Constraints` block.

## Implementation Examples 

### Scenario A: Filtering Noise
**User:** "Hey, I'm having a coffee. It's raining outside. Anyway, build me a prompt for a Python script that scrapes LinkedIn but don't use BeautifulSoup."
**Skill Execution:**
- **Discarded:** Coffee, Weather.
- **Retained:** Task (Python Script), Objective (Scrape LinkedIn), Negative Constraint (No BeautifulSoup).

### Scenario B: Constraint Persistence
**User:** "Remember for this whole session, our tone is 'Cynical Tech Bro'."
**Skill Execution:**
- **Locking:** Apply `# STYLE: Cynical Tech Bro` to every subsequent output until the session is reset.

## Guardrails
- **Privacy:** Never cache or store PII (Personally Identifiable Information) in the `Active_Context_Block`.
- **Conflict Resolution:** If a new instruction contradicts a "Locked Constraint," the agent MUST pause and ask the user for clarification before proceeding.

## Variables Managed
- `[USER_BRAND_VOICE]`
- `[BANNED_PHRASES]`
- `[TECHNICAL_STACK_LIMITS]`
- `[HISTORICAL_CONTEXT_ID]`
