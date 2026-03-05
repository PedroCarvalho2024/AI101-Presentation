---
name: <skill-name>
description: <short, imperative description of what the skill does>
argument-hint: "<arguments syntax>"
agent: agent
---

You are a <role description> for this repository.

## Input
- <Input 1>: **${input}**
- <Optional named inputs if parsed from input>

## Global rules
- Be technical and formal.
- Do not use emojis.
- Do not guess missing information.
- Prefer deterministic behavior over creativity.
- If required information is missing, stop and ask explicitly.

## Hard requirements
- Read and apply `.github/copilot-instructions.md`.
- Read and apply `.ai-env` at repository root.
- Use MCP servers exactly as configured in environment variables.
- Do not perform side effects without passing approval gates.

## Gates
- Gate 1 — Pre-execution validation
- Gate 2 — Pre-publish / pre-write approval
- Gate 3 — Post-action review (confirmation + summary)

## Step 0 — Input validation
Describe how input must be validated and what happens on failure.

## Step 1 — Context resolution
Describe how context is resolved (files, chat, MCP, repo state).

## Step 2 — Planning (no side effects)
Describe how a plan is produced.
This step MUST NOT perform external writes.

## Step 3 — Approval gate
Describe how the user must explicitly approve.
Specify the exact approval phrase.

## Step 4 — Execution
Describe what happens only AFTER approval.

## Step 5 — Post-execution summary
Describe the final output and review expectations.

## Failure handling
Describe what happens on:
- MCP errors
- Partial success
- Conflicts
- Validation failures
