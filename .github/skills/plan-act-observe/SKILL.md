---
name: plan-act-observe
description: 'This skill implements the Agentic Reasoning Core. It prevents the model from "shooting from the hip" by enforcing a mandatory internal reflection cycle. The agent must simulate potential outcomes, execute the most logical path, and then critique its own output against user requirements before final delivery.'
---
# Plan-Act-Observe Agentic Reasoning Core Skill

## Metadata
- **ID:** SKILL-PAO
- **Domain:** Cognitive Architecture / Multi-Step Reasoning

## Description
This skill implements the **Agentic Reasoning Core**. It prevents the model from "shooting from the hip" by enforcing a mandatory internal reflection cycle. The agent must simulate potential outcomes, execute the most logical path, and then critique its own output against user requirements before final delivery.

## Operational Logic (The Reasoning Engine)
The Agent must follow this three-stage recursive loop for any complex prompt generation task:

### 1. Plan (Strategy Formulation)
- **Mental Sandbox:** Before writing the prompt, the agent must define:
    - The "Golden Thread": The single most important outcome the prompt must achieve.
    - The "Edge Cases": Where the prompt might fail (e.g., being too wordy, missing technical nuances).
- **Architecture Choice:** Select the best prompt engineering technique (e.g., Few-Shot, Chain-of-Thought, ReAct, or Self-Consistency).

### 2. Act (Drafting & Execution)
- **Drafting:** Generate the prompt based on the Strategy.
- **Variable Alignment:** Ensure all `[USER_INPUT_VARIABLES]` are logically placed and explained.
- **Constraint Adherence:** Cross-reference the draft against all `SKILL-CONTEXT-001` locked constraints.

### 3. Observe (Self-Correction & Validation)
- **The Critic Mode:** The agent must ask itself: "If I were a 'dumb' model receiving this prompt, would I hallucinate or fail?"
- **Scoring:** If the prompt scores low on clarity or precision, the agent must perform a **Loop-Back** to the Plan stage to refine the logic.
- **Output:** Present the prompt to the user only after the "Critic" passes the version.

## Implementation Examples for Copilot

### Scenario A: Complex Coding Prompt
**User:** "Build a prompt for a React component that handles real-time WebSockets."
**Skill Execution:**
- **Plan:** Strategy: Chain-of-Thought. Strategy: Ensure error handling is included.
- **Act:** Drafts the prompt with a detailed system role.
- **Observe:** Critic notices the prompt forgot to mention `cleanup` effects. Agent loops back to fix the draft.

## Guardrails
- **No Infinite Loops:** Maximize reasoning cycles to 3 loops before requiring human intervention.
- **Transparency:** The agent must be able to explain its "Line of Reasoning" if asked: "Why did you choose this structure?"
- **Accuracy over Speed:** Prioritize logical soundness over immediate response time.

## Variables Managed
- `[INTERNAL_STRATEGY]`
- `[CRITIC_SCORE]`
- `[REASONING_CHAIN]`
- `[ITERATION_COUNT]`