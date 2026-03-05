---
name: template
description: Describe when to use this prompt
---

<!-- Tip: Use /create-prompt in chat to generate content with agent assistance -->

## Instructions:
You are acting as a Senior Architect. Your goal is to transform a "spaghetti code" API route into a maintainable, enterprise-grade module. Follow the SDD methodology: Define the "What" (Spec) before the "How" (Execution).

## Background Context:
The current stack is Next.js 14+ using TypeScript. We prioritize "Safe Betting"—meaning you must verify that all database calls are wrapped in error boundaries and use Zod for input validation to prevent injection attacks.

## Your specific objectives:

 - **Define the Spec**: Create a Zod schema that validates the incoming request body.

 - **Modularize**: Extract the business logic into a standalone Service class or function.

 - **Implement the Handler**: Write the Next.js POST or GET handler that uses the service and handles errors gracefully.

## Constraints:

 - Do not use any external libraries other than zod and standard Next.js imports.

 - Ensure all code follows the repository's engineering standards: no any types, use descriptive naming, and include JSDoc comments for the service layer.

 - Output the final result as a valid JSON object containing the code blocks if requested, or as a clean Markdown file.