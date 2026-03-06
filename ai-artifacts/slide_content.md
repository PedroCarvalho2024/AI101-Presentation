# AI 101 - Technical Briefing: LLM Integration & Workflows
**Theme:** Technical, professional, modern AI engineering
**Role:** Senior AI Solutions Architect

---

## Slide 1 - Cover

**Heading:** AI 101: A Workshop on Modern AI Concepts

**Subtitle:** From Foundations to Agentic Systems

**Visuals:** Clean background with a neural-net path graphic in blue tones

**Notes:**
Welcome to AI 101. This workshop is a technical primer designed for practitioners to move beyond buzzwords and understand the architecture, prompting, and deployment of modern AI systems. We will cover the full spectrum from foundational concepts to advanced agentic patterns, RAG pipelines, and security considerations.

---

## Slide 2 - Agenda

**Heading:** Technical Briefing: LLM Integration & Workflows

**Content:**
- The Basics: Evolution, Prompts and Models
- The Controls: Instructions, Context and Consumption
- The Architecture: Agents, Skills and Personas
- The Workflow: Methodologies (SDD, BMAD)
- The Safeguards: RAG, Code Review and Security

**Notes:**
This agenda provides a roadmap for moving from conceptual foundations through practical engineering patterns and into advanced retrieval architectures and security.

---

## Slide 3 - AI Evolution: From Passive Tool to Active Partner

**Heading:** AI Has Evolved From Rule-Based Responses to Autonomous, Multi-Step Reasoning

**Content:**
- Static Scripts: Hard-coded logic; fixed responses with no learning (e.g., FAQ bots)
- Generative AI: Conversational and probabilistic; open-ended text, code, and images (e.g., early large language models)
- Agentic Workflows: Autonomous and goal-oriented; uses tool-use and planning loops to act and iterate

**Notes:**
The shift to agentic AI is the most important architectural transition today. Unlike generative models that just respond, agentic systems plan, act, and observe using tools and memory.

---

## Slide 4 - The Art of Prompting: R-C-T-C

**Heading:** The Quality of Your Prompt Determines the Quality of Your Output

**Content:**
- Role: Who is the AI? (e.g., "Act as a Senior Architect")
- Context: Background info (e.g., "Given the current Next.js stack")
- Task: Actionable instruction (e.g., "Refactor the API route")
- Constraints: Format and limits (e.g., "Return only JSON")

**Notes:**
The R-C-T-C (Role-Context-Task-Constraint) framework is a reliable scaffold for consistent, high-quality outputs. Adding few-shot examples can further improve precision.

---

## Slide 5 - Model Comparison: Speed vs. Reasoning

**Heading:** Matching Model Capabilities to Task Profiles

**Content:**
| Model Type | Examples (2025-26) | Best For | Context/Latency |
| :--- | :--- | :--- | :--- |
| Fast help with simple/repetitive tasks | Claude Haiku 4.5 | Syntax checks, simple Q&A | Low Latency |
| General-purpose coding/writing | GPT-5.3-Codex | Daily coding, docs, unit tests | The Daily Driver |
| Deep Reasoning & Debugging | Claude Opus 4.6 | Architecture, debugging | High Latency and Cost |

**Notes:**
Model selection is a trade-off between speed and depth. Lightweight models are ideal for edge tasks; deep reasoning models are necessary for complex system architecture.

---

## Slide 6 - Copilot Instructions

**Heading:** Enterprise Control Plane for AI Behavior

**Content:**
- Location: Defined in .github/copilot-instructions.md
- Persistent Context: Rules apply to every chat session
- Repository Level: Enforces engineering standards (for example, "Use TypeScript, No SQL")

**Notes:**
Copilot instructions allow organizations to codify standards, ensuring consistent and policy-compliant output across all developer workflows.

---

## Slide 7 - Consumption & Token Economics

**Heading:** Balancing Reasoning Depth with Quota Costs

**Content:**
- Standard vs Premium: High-reasoning models often consume more quota
- Multiplier: Smart models (Claude Opus 4.6) may have a higher multiplier on token costs
- Strategy: Use 'Auto' mode to balance cost and performance automatically

**Notes:**
Efficient AI engineering requires understanding token economics. Use expensive reasoning models only when task complexity justifies the cost multiplier.

---

## Slide 8 - Context & Hallucinations

**Heading:** Context Below 70% Prevents Hallucinations

**Content:**
- Context Rot: Utilizing more than 70% of context capacity degrades reasoning quality
- Hallucinations: AI inventing plausible but factually incorrect information
- Mitigation: Provide a clean context stream using RAG and reduce temperature

**Notes:**
Models begin to forget or conflate information as the context window fills. The 70% rule is a practical heuristic for maintaining attention quality.

---

## Slide 9 - Templates & Standardization

**Heading:** Templates Standardize Quality

**Content:**
- Don't Reinvent the Wheel: Use structured prompt templates for reproducibility
- Storage: Keep prompts in prompts.md for team collaboration
- Force Formats: Require explicit JSON or Markdown for downstream compatibility

**Notes:**
Standardized templates are the engineering discipline that separates ad-hoc use from production-grade AI systems.

---

## Slide 10 - Agents & Subagents

**Heading:** Decomposing Complexity Into Coordinated Action

**Content:**
- Agent (The Manager): Orchestrates goals and delegates tasks
- Subagents: Specialized workers for Research, Coding, and Review
- Execution Loop: Plan -> Test -> Fix
- Parallel Execution: Subagents can work simultaneously on partitioned tasks

**Notes:**
The orchestrator-subagent pattern mirrors microservices. Each subagent has a single responsibility and communicates via structured messages.

---

## Slide 11 - Personas: Changing the Lens

**Heading:** Personas Define Who the AI Is

**Content:**
- Senior Architect: Focuses on system design and trade-offs
- QA Engineer: Focuses on edge cases and failure modes
- Security Analyst: Focuses on vulnerabilities and injection risks
- Implementation: Define these identities in persona.md

**Notes:**
Personas ensure domain expertise and a consistent voice. Composing multiple personas can assist in complex cross-domain tasks.

---

## Slide 12 - Skills

**Heading:** Skills Define What the AI Can Do

**Content:**
- Definition: Portable capabilities consisting of instructions and scripts
- Standard: Define skills in SKILL.md for reusability
- Examples: Database migration, terminal access, web search

**Notes:**
Skills are the tool-belt of callable capabilities and map to tools or connectors that let the AI interact with systems and the web.

---

## Slide 13 - MCP (Model Context Protocols)

**Heading:** Standardizing Interoperability Between Models and Tools

**Content:**
- Standardized Method: Defines how models obtain context from external sources
- Explicit Protocols: Handles context passing and prevents ambiguity
- Interoperability: Facilitates communication between different models and specialized tools

**Notes:**
MCP reduces ambiguity in complex systems where multiple models must share a unified context.

---

## Slide 14 - Methodologies: SDD & BMAD

**Heading:** Translating Business Intent Into Executable Architecture

**Content:**
- SDD (Spec-Driven Development): Define the spec (what), validate the plan, execute the code (how)
- BMAD: Business, Model, Agent, Data - an AI-driven development lens
- Agile and iterative: Use AI for code, tests, and validation in short cycles

**Notes:**
BMAD ensures AI development aligns with business goals while SDD brings software engineering rigor to prompt and model management.

---

## Slide 15 - RAG: Retrieval-Augmented Generation

**Heading:** Grounding AI in Facts via Private Data

**Content:**
- Process: Retrieve (private data) -> Augment (the prompt) -> Generate (the response)
- Goal: Eliminate hallucinations by using a database as a source of truth
- Data Sources: Database servers, PDFs, local files

**Notes:**
RAG is the standard for enterprise AI. It decouples knowledge from model weights so you can update knowledge without retraining.

---

## Slide 16 - GraphRAG: Beyond Keywords

**Heading:** Understanding Relationships via Knowledge Graphs

**Content:**
- Relational Intelligence: Map entities such as people, code, and files
- Multi-hop Reasoning: Traverse subgraphs to answer interconnected queries
- Visual: Show nodes and relationship paths between modules and teams

**Notes:**
GraphRAG excels in domains where context is relational rather than purely textual, such as legal or enterprise architecture.

---

## Slide 17 - AI Code Review Tools

**Heading:** AI as the First Line of Defense

**Content:**
- Automated PR Summaries: Explain code changes quickly
- Stylistic and Anti-pattern Detection: Catch common errors before review
- Security Scanning: Detect leaked secrets and vulnerabilities

**Notes:**
AI-powered review tools reduce reviewer fatigue and keep obvious bugs and security flaws out of the main branch.

---

## Slide 18 - Security & Safe Betting

**Heading:** Trust but Verify

**Content:**
- Data Privacy: Ensure PII is not leaked into public models
- Injection Attacks: Prevent malicious input from hijacking model behavior
- Core Principle: AI is a suggestion engine, not a truth engine

**Notes:**
Every production system must include input/output sanitization and audit logs to defend against OWASP LLM Top 10 risks.

---

## Slide 19 - Summary & Q&A

**Heading:** Architectural Thinking Over Prompt Creativity

**Takeaways:**
- Prompt with Structure: Use R-C-T-C
- Control with Context: Manage context windows effectively
- Architect with Agents: Use modular skills and personas
- Verify with SDD: Treat AI systems as engineered products

**Notes:**
Apply architectural rigor: codify instructions, ground with RAG, design modular agents, and enforce security and evaluation as part of CI. Q and A.

