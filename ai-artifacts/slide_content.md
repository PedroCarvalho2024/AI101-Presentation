# AI 101 — Slide Content Outline
**Theme:** Light, technical, professional
**Role:** Senior AI Solutions Architect
**Slide Count:** 12

---

## Slide 1 — Cover

**Title:** AI 101
**Subtitle:** From Foundations to Agentic Systems
**Presenter Role:** Senior AI Solutions Architect
**Visual style:** Clean light background, bold sans-serif typography, subtle circuit/neural-net accent graphic in muted blue tones

**Notes:**
Welcome to AI 101 — a technical primer designed for practitioners and decision-makers who want to move beyond buzzwords and understand how modern AI systems are architected, prompted, and deployed. This session covers the full spectrum from foundational concepts to advanced agentic patterns, RAG pipelines, and security considerations.

---

## Slide 2 — Index / Agenda

**Heading:** What We'll Cover Today

| # | Topic |
|---|-------|
| 1 | AI Evolution: Static → Agentic |
| 2 | Prompts & Prompt Engineering |
| 3 | Model Comparison |
| 4 | Copilot Instructions & Context |
| 5 | Prompt & Output Templates |
| 6 | Agents, Subagents & Personas |
| 7 | Skills & Spec Kits |
| 8 | RAG & GraphRAG |
| 9 | Code Review Tools |
| 10 | Security in AI Systems |
| 11 | Conclusion |

**Notes:**
This index gives you a roadmap for the session. We move from conceptual foundations through practical engineering patterns, then into advanced retrieval architectures, tooling, and security. Each section builds on the previous one, so by the end you'll have a coherent mental model of the modern AI stack.

---

## Slide 3 — AI Evolution: From Static to Agentic

**Heading:** AI Has Evolved From Rule-Based Responses to Autonomous, Multi-Step Reasoning

**Content:**

**Four Generations of AI Capability:**

| Stage | Paradigm | Capability | Example |
|-------|----------|------------|---------|
| **Static** | Rule-based / scripted | Fixed responses, no learning | FAQ bots, decision trees |
| **Generative** | LLM inference | Open-ended text, code, images | GPT-3, DALL-E |
| **Instructable** | Fine-tuned + RLHF | Role-aware, steerable output | GPT-4, Claude, Gemini |
| **Agentic** | Tool-use + planning loops | Multi-step tasks, memory, APIs | AutoGPT, Copilot Agents |

**Key insight:** Agentic AI doesn't just respond — it **plans, acts, observes, and iterates** using tools, memory, and subagents.

**Notes:**
The shift from static to agentic is the single most important architectural transition in modern AI. Static systems were deterministic and brittle. Generative models introduced probabilistic, open-ended output. Instructable models added alignment and steerability. Agentic systems go further: they decompose goals into subtasks, invoke external tools (APIs, code interpreters, search), maintain state across turns, and delegate to specialized subagents. This is the paradigm that underpins Copilot, AutoGPT, and enterprise AI orchestration platforms.

---

## Slide 4 — Prompts & Model Comparison

**Heading:** The Quality of Your Prompt Determines the Quality of Your Output

**Left column — Prompt Engineering Fundamentals:**

- **Role** — Define who the model is: `"Act as a Senior Security Engineer..."`
- **Context** — Provide relevant background and constraints
- **Task** — State the specific action clearly and unambiguously
- **Format** — Specify output structure: JSON, Markdown table, bullet list
- **Examples** — Few-shot examples dramatically improve precision

**Right column — Model Comparison (2025):**

| Model | Strengths | Context Window | Best For |
|-------|-----------|----------------|----------|
| GPT-4.1 | Reasoning, code | 128K | Complex tasks, agents |
| Claude 3.7 | Long docs, safety | 200K | Document analysis |
| Gemini 2.5 | Multimodal, speed | 1M | Large-scale retrieval |
| Llama 3.3 | Open-source, cost | 128K | On-prem, fine-tuning |
| Mistral | Lightweight, fast | 32K | Edge, low-latency |

**Notes:**
Prompt engineering is the primary interface between human intent and model behavior. The Role-Context-Task-Format-Examples (RCTFE) framework is a reliable scaffold for consistent, high-quality outputs. Model selection is equally important: GPT-4.1 excels at multi-step reasoning and code generation; Claude 3.7 handles very long documents with high fidelity; Gemini 2.5 Pro offers the largest context window at 1M tokens, ideal for RAG over massive corpora; Llama 3.3 is the go-to for on-premises deployments where data sovereignty is required.

---

## Slide 5 — Copilot Instructions & Context Management

**Heading:** Copilot Instructions Shape Behavior; Context Below 70% Prevents Hallucinations

**Left column — Copilot Instructions:**

- Defined in `.github/copilot-instructions.md` or system prompt
- Set **persona**, **coding standards**, **output format**, and **guardrails**
- Scoped at: Repository level · Organization level · User level
- Example directives:
  - `"Always add JSDoc comments to exported functions"`
  - `"Prefer functional React components with TypeScript"`
  - `"Never suggest deprecated APIs"`

**Right column — Context & Hallucination Control:**

- **Context window** = total tokens the model can "see" at once
- **Target: keep context utilization below 70%**
  - Leaves headroom for reasoning and response generation
  - Reduces compression artifacts and attention degradation
- **Hallucination** = model generates plausible but factually incorrect output
  - Cause: insufficient grounding, context overflow, ambiguous prompts
  - Mitigations: RAG, temperature reduction, explicit grounding instructions, self-consistency checks

**Notes:**
Copilot instructions are the enterprise control plane for AI behavior. By codifying standards in instruction files, teams ensure consistent, policy-compliant output across all developers. On context management: the 70% rule is a practical heuristic — models begin to "forget" or conflate information as the context window fills. Keeping utilization below 70% preserves attention quality. Hallucinations are the most dangerous failure mode in production AI; they are best mitigated through retrieval-augmented grounding, structured output schemas, and human-in-the-loop validation for high-stakes decisions.

---

## Slide 6 — Prompt & Output Templates · Agents & Subagents

**Heading:** Templates Standardize Quality; Agents Decompose Complexity Into Coordinated Action

**Left column — Prompt & Output Templates:**

**Prompt Template Structure:**
```
ROLE: [Persona definition]
CONTEXT: [Background + constraints]
TASK: [Specific instruction]
FORMAT: [Output schema / structure]
EXAMPLES: [1–3 few-shot samples]
```

**Output Template Types:**
- **Structured JSON** — for API consumption and downstream processing
- **Markdown Report** — for human-readable documentation
- **Code Block** — for executable artifacts with inline comments
- **Tabular Summary** — for comparison and decision support

**Right column — Agents & Subagents:**

```
Orchestrator Agent
├── Planning Subagent      → Decomposes goal into tasks
├── Research Subagent      → Web search, RAG retrieval
├── Code Subagent          → Writes, tests, debugs code
├── Review Subagent        → Validates output quality
└── Memory Subagent        → Manages context & state
```

- **Orchestrator** holds the goal and delegates
- **Subagents** are specialized, tool-equipped workers
- Communication via **structured messages** (JSON schema)
- State managed via **short-term** (context) and **long-term** (vector DB) memory

**Notes:**
Templates are the engineering discipline that separates ad-hoc AI use from production-grade AI systems. Standardized prompt templates ensure reproducibility; output templates ensure downstream compatibility. On the agentic side: the orchestrator-subagent pattern mirrors microservices architecture — each subagent has a single responsibility, a defined interface, and can be independently upgraded or replaced. This is the architecture behind Microsoft Copilot Studio, LangGraph, and AutoGen multi-agent frameworks.

---

## Slide 7 — Personas & Skills

**Heading:** Personas Define Who the AI Is; Skills Define What It Can Do

**Left column — Personas:**

A **Persona** is a named, role-specific identity configuration:

```yaml
persona: "Senior Security Architect"
tone: "precise, risk-aware, formal"
expertise: ["zero-trust", "SIEM", "threat modeling"]
constraints:
  - "Never recommend deprecated protocols"
  - "Always cite CVE references for vulnerabilities"
  - "Flag any GDPR-relevant data handling"
```

- Personas ensure **consistent voice** and **domain expertise** across sessions
- Can be scoped to teams, projects, or individual workflows
- Composable: combine multiple personas for cross-domain tasks

**Right column — Skills:**

A **Skill** is a reusable, modular capability unit:

| Skill | Description | Trigger |
|-------|-------------|---------|
| `web-search` | Live internet retrieval | "search for..." |
| `code-interpreter` | Execute Python/JS in sandbox | "run this code" |
| `document-reader` | Parse PDF/Word/Excel | "analyze this file" |
| `image-generator` | Create visuals from text | "generate an image" |
| `api-caller` | Invoke REST/GraphQL endpoints | "call the API" |
| `memory-recall` | Retrieve from vector store | "remember when..." |

**Notes:**
Personas and skills are the two axes of agent customization. Personas answer "who is the agent?" — they encode domain knowledge, communication style, and behavioral guardrails. Skills answer "what can the agent do?" — they are the tool-belt of callable capabilities. In Microsoft Copilot Studio, skills map to actions and connectors. In LangChain, they map to tools. The combination of a well-defined persona and a curated skill set produces an agent that is both trustworthy and capable.

---

## Slide 8 — Spec Kits: BMAD & Open Spec

**Heading:** Spec Kits Translate Business Intent Into Executable AI Architecture

**What is a Spec Kit?**
A **Spec Kit** is a structured documentation framework that bridges business requirements and AI system design. It ensures alignment between stakeholders, architects, and AI agents.

**BMAD Method (Business, Model, Agent, Data):**

| Layer | Focus | Key Artifacts |
|-------|-------|---------------|
| **B**usiness | Goals, KPIs, constraints | PRD, user stories, success metrics |
| **M**odel | AI model selection & config | Model card, prompt templates, eval criteria |
| **A**gent | Agent design & orchestration | Agent graph, persona definitions, skill registry |
| **D**ata | Data sources, RAG config, governance | Data catalog, embedding strategy, access controls |

**Open Spec:**
- Open, version-controlled specification format for AI systems
- Defines: system prompt, tools, memory config, guardrails, eval harness
- Enables **reproducibility**, **auditability**, and **team collaboration**
- Analogous to OpenAPI for REST APIs — a contract for AI behavior

**Notes:**
The BMAD method is a practitioner framework for decomposing AI projects into four tractable layers. Starting with Business ensures the AI system is solving the right problem. Model selection is driven by the task profile, not hype. Agent design specifies the orchestration topology. Data governance is often the most underestimated layer — poor data quality is the leading cause of AI project failure. Open Spec brings software engineering discipline to AI: version control your prompts, your agent graphs, and your eval criteria just as you version control your code.

---

## Slide 9 — RAG & GraphRAG

**Heading:** RAG Grounds AI in Facts; GraphRAG Adds Relational Intelligence

**Left column — RAG (Retrieval-Augmented Generation):**

```
User Query
    │
    ▼
[Embedding Model] → Query Vector
    │
    ▼
[Vector Database] → Top-K Relevant Chunks
    │
    ▼
[LLM] + [Retrieved Context] → Grounded Response
```

- Eliminates hallucinations by grounding responses in retrieved documents
- Supports: PDFs, wikis, databases, APIs, SharePoint, Confluence
- Key metrics: **Recall@K**, **MRR**, **Faithfulness**, **Answer Relevance**

**Right column — GraphRAG:**

```
Documents → Entity Extraction → Knowledge Graph
                                      │
User Query → Graph Traversal → Relevant Subgraph
                                      │
                              LLM + Subgraph → Response
```

- Extends RAG with **entity relationships** and **graph traversal**
- Excels at: multi-hop reasoning, organizational knowledge, causal chains
- Microsoft GraphRAG: community detection + summarization at scale
- **When to use GraphRAG:** complex, interconnected knowledge domains (legal, medical, enterprise architecture)

**Notes:**
RAG is now the standard architecture for enterprise AI that requires factual accuracy. By retrieving relevant chunks from a vector database at inference time, RAG decouples knowledge from model weights — you can update your knowledge base without retraining. GraphRAG goes further by representing knowledge as a graph of entities and relationships. This enables multi-hop reasoning: "What are the security implications of the vendor's API, given our data classification policy and the recent CVE?" — a query that requires traversing multiple connected concepts. Microsoft's open-source GraphRAG library is the leading implementation for enterprise-scale deployments.

---

## Slide 10 — Code Review Tools & Security

**Heading:** AI-Powered Code Review and Security Controls Are Now Essential Engineering Infrastructure

**Left column — Code Review Tools:**

| Tool | Capability | Integration |
|------|------------|-------------|
| **GitHub Copilot** | Inline suggestions, PR review | VS Code, GitHub |
| **CodeRabbit** | Automated PR summaries, issue detection | GitHub, GitLab |
| **Cursor** | Full-codebase context, refactoring | IDE |
| **Snyk** | Vulnerability scanning, SAST | CI/CD pipeline |
| **SonarQube + AI** | Code quality + AI-assisted fixes | Jenkins, Azure DevOps |
| **Amazon CodeGuru** | Performance & security reviewer | AWS CodeCommit |

**Right column — Security in AI Systems:**

**OWASP LLM Top 10 — Critical Risks:**
1. **Prompt Injection** — Malicious input hijacks model behavior
2. **Insecure Output Handling** — Unvalidated AI output executed downstream
3. **Training Data Poisoning** — Corrupted data degrades model integrity
4. **Model Denial of Service** — Resource exhaustion via adversarial inputs
5. **Sensitive Information Disclosure** — PII/secrets leaked in responses

**Mitigations:**
- Input/output sanitization and schema validation
- Least-privilege tool access for agents
- Audit logging of all AI interactions
- Human-in-the-loop for high-stakes decisions
- Red-teaming and adversarial testing

**Notes:**
AI code review tools have matured rapidly. GitHub Copilot's PR review feature can now summarize changes, flag potential bugs, and suggest improvements inline. CodeRabbit provides automated, contextual PR feedback that reduces reviewer fatigue. On security: the OWASP LLM Top 10 is the authoritative reference for AI-specific threat modeling. Prompt injection is the most prevalent attack vector — an attacker embeds instructions in user input that override the system prompt. Defense requires strict input validation, output schema enforcement, and sandboxed tool execution. Every production AI system should have an audit log of all model interactions for forensic and compliance purposes.

---

## Slide 11 — Copilot Agents Ecosystem

**Heading:** The Copilot Ecosystem Connects AI Agents Across Every Layer of the Enterprise Stack

**Microsoft Copilot Ecosystem:**

```
Microsoft 365 Copilot
├── Word / Excel / PowerPoint / Outlook / Teams
│
GitHub Copilot
├── Code completion · PR Review · Copilot Chat · Workspace
│
Copilot Studio
├── Custom Agents · Skills · Connectors · Knowledge Sources
│
Azure AI Foundry
├── Model Catalog · Prompt Flow · Evaluation · Deployment
│
Copilot+ PC
└── On-device inference · Recall · Cocreator
```

**Deployment Patterns:**
- **Embedded** — Copilot within existing Microsoft apps
- **Custom Agent** — Built in Copilot Studio, deployed to Teams/web
- **Autonomous Agent** — Trigger-based, runs without human initiation
- **Multi-Agent** — Orchestrator delegates to specialist agents

**Notes:**
The Microsoft Copilot ecosystem is the most widely deployed enterprise AI platform, reaching over 300 million Microsoft 365 users. Understanding its layers is essential for enterprise AI architects. Copilot Studio is the low-code/pro-code platform for building custom agents with specific knowledge sources, skills, and connectors to enterprise systems. Azure AI Foundry is the MLOps platform for model evaluation, fine-tuning, and production deployment. The shift to autonomous and multi-agent patterns represents the frontier of enterprise AI deployment in 2025–2026.

---

## Slide 12 — Conclusion & Next Steps

**Heading:** AI Mastery Requires Architectural Thinking, Not Just Prompt Creativity

**Key Takeaways:**

| Concept | Core Principle |
|---------|---------------|
| **AI Evolution** | We are in the Agentic era — design for autonomy and orchestration |
| **Prompts & Models** | Match model capabilities to task profiles; engineer prompts systematically |
| **Context & Hallucinations** | Keep context < 70%; ground responses with RAG |
| **Agents & Skills** | Decompose complexity; build modular, composable agent systems |
| **Spec Kits** | Treat AI systems as engineered products with versioned specifications |
| **RAG / GraphRAG** | Retrieval is the foundation of factual, trustworthy AI |
| **Security** | Apply OWASP LLM Top 10; audit, validate, and red-team continuously |

**Your Next Steps:**
1. Define your **Copilot Instructions** for your team's repositories
2. Build a **RAG pipeline** over your internal knowledge base
3. Design your first **multi-agent workflow** using BMAD
4. Establish an **AI security review** process in your CI/CD pipeline

**Notes:**
The central message of AI 101 is this: AI is now an engineering discipline, not a magic box. The teams that win are those who apply the same rigor to AI systems that they apply to software architecture — versioned specifications, modular design, security-first thinking, and continuous evaluation. Start small: pick one use case, apply the BMAD framework, build a RAG-grounded agent with clear persona and skills, and measure outcomes against defined KPIs. Then scale what works. The agentic era is here — architect for it deliberately.

---
