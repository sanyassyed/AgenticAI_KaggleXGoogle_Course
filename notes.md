# 5 Day Course Notes
## Day 1 - Introduction to AI Agents
* [Lab 1a](https://www.kaggle.com/code/sanyasyed/day-1a-from-prompt-to-action-sanyasyed): From Prompt to Action
* [Lab 1b](https://www.kaggle.com/code/sanyasyed/day-1b-agent-architectures-sanyasyed): Agent Architecture
* [White Paper- Introduction to Agents](https://www.kaggle.com/whitepaper-introduction-to-agents)
* [Podcast- Introduction to Agents](https://www.youtube.com/watch?v=zTxvGzpfF-g)
  
### 🧩 Core Components

| **Component**                                          | **Role**                             | **Description**                                                                                                                                   |
| ------------------------------------------------------ | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Model (Brain / Reasoning)**                          | LLM (manages context and reasoning)  | Thinks, plans, and decides what to do next based on input and memory.                                                                             |
| **Tools (Hands)**                                      | APIs, Vector stores, SQL, Web access | Extend the model’s capability to interact with the outside world.                                                                                 |
| **Orchestration (Coordinator / Conductor / Governor)** | Manages flow                         | Calls the tools, feeds results back to the model, and decides when to think, act, or wait. Often managed via frameworks like LangChain or CrewAI. |

---

### ⚙️ REACT

* **Meaning:** Reasoning + Acting
* **Goal:** Execute a mission through a **Chain of Thought**

**Cycle:**

1. **Think** — Model reasons or plans a step
2. **Act** — Executes a tool or API call
3. **Observe** — Collects results or environment feedback
4. **Repeat** — Continues reasoning until task completion

> 🔁 *ReACT alternates between reasoning and acting to ensure transparent, explainable decision-making.*

---

### 📏 Key Metrics

* **Security**
* **Quality**
* **Reliability**

---

### 🧠 System Concepts

1. **Anatomy:** Model + Tools + Orchestration
2. **Taxonomy:** Simple agent system → Multi-agent system
3. **Architectural Design:** How components connect and interact
4. **Building for Production:** Secure, scalable, and observable

**Lifecycle:** Build → Deploy → Manage an Agent

---

### 🧭 Agentic Systems

* Agents **plan and act** independently using reasoning and tools.
* **Tool outputs** are appended to the context (prompt) for the next reasoning step.

---

### 🔁 5-Step Operational Loop

1. **Get the Mission** — Identify the task
2. **Scan the Scene** — Gather data, identify gaps or resources
3. **Think it Through** — Plan a reasoning path
4. **Take Action** — Execute chosen tools or actions
5. **Observe & Iterate** — Learn from feedback and improve

---

### 🧮 Taxonomy of Agentic Systems

*(How complex should the agent be?)*

|   **Level** | **Description**                  | **Notes**                | **Example**                              |
| ----------: | -------------------------------- | ------------------------ | ---------------------------------------- |
| **Level 0** | Core Reasoning System            | No tools (“no hands”)    | Pure reasoning — model only              |
| **Level 1** | Connected Problem Solver         | Uses RAG or APIs         | Get current weather info                 |
| **Level 2** | Strategic Problem Solver         | Context engineering      | Suggest best coffee shop between 2 areas |
| **Level 3** | Collaborative Multi-Agent System | Manager–Specialist model | Project Manager Agent with sub-agents    |
| **Level 4** | *Self-Evolving Agents*           | *(Future concept)*       | Agents that self-improve over time       |

---

### 🏗️ Architectural Design

#### 🧩 Model

* **Superior reasoning**
* **Reliable tool use**
* **Optimized for quality, speed, and cost**
  → *Test models for task suitability.*

**Model Routing Strategy:**
Route each agent’s request to the **most appropriate model** based on performance, cost, and modality.

**Examples:**

* Gemini 2.5 Pro
* Gemini 2.5 Flash
* Gemini Live Model
* Cloud Vision API
* Speech-to-Text API

**AgentOps:**

* Build agents that can be upgraded easily using **CI/CD** practices.

---

#### 🧰 Tools for Retrieval & Action

##### 🔍 Retrieval Tools

* **RAG (Retrieval-Augmented Generation):** Vector DB or knowledge graphs
* **Natural Language to SQL:** Allows agents to query databases

##### ⚙️ Action Tools

* **APIs:** Execute actions (e.g., search, send email)
* **HITL (Human in the Loop):** Human feedback via SMS or UI

##### **Function Calling:**
* For an agent to reliably do “function calling” and use tools, it needs clear instructions, secure connections, and orchestration.
* Fuction calling can be done via **MCP (Model Context Protocol)** — open standard for connecting AI to external systems
* Can be implemented using **ADK (Agent Development Kit)** or similar frameworks

---

#### The Orchestration Layer
##### Core Design Choices
##### Instruct with Domain Knowledge and Persona
##### Augment with Context
* **Purpose:** Augment the agent with context and persona

| **Type**              | **Function**                                      |
| --------------------- | ------------------------------------------------- |
| **Short-term memory** | Scratchpad for immediate actions and observations |
| **Long-term memory**  | Persistent storage (e.g., via RAG and vector DBs) |


##### 🕸️ Multi-Agent System Design Patterns

**Coordinator Pattern:**

* **Manager Agent:** Oversees process and delegates work
* **Specialist Agents:** Handle domain-specific subtasks

---

### 🧪 Testing & Debugging

* **FMOps (Foundation Model Ops):**
  * Manage and monitor large models efficiently.
  * Includes evaluation, versioning, and deployment.

* 🔧 Agent Ops
  * Evaluate agent performance and reasoning quality using another LLM (*LLM-as-a-judge*).
  * Use telemetry and benchmarks for human validation.

---

### Introduction: Models, Tools and Agents 
* Tools become the eyes and hands of the foundation models

### 💬 Key Terminologies

* **Interoperability:** The ability of different systems and applications to communicate and work together effectively.
* **MCP (Model Context Protocol)** — open standard for connecting AI to external systems
* **Agent Development Kit (ADK)** - a flexible and modular framework for developing and deploying AI agents

---

## Day 2 - Agent Tools & Interoperability with Model Context Protocol (MCP)
* [Lab 2a](https://www.kaggle.com/code/sanyasyed/day-2a-agent-tools-sanyasyed): Agent Tools
* [Lab 2b](https://www.kaggle.com/code/sanyasyed/day-2b-agent-tools-best-practices-sanyasyed): Agent Tools Best Practices
* [White Paper- Agent Tools & Interoperability with MCP](https://www.kaggle.com/whitepaper-agent-tools-and-interoperability-with-mcp) 
* [Podcast- Agent Tools & Interoperability with MCP](https://www.youtube.com/watch?v=Cr4NA6rxHAM)
  
### Introduction: Models, Tools and Agents 
* Tools become the eyes and hands of the foundation models

###  Agent Tools vs Sub-Agents: What's the Difference?
This is a common question! Both involve using multiple agents, but they work very differently:

Agent Tools (what we're using):

Agent A calls Agent B as a tool
Agent B's response goes back to Agent A
Agent A stays in control and continues the conversation
Use case: Delegation for specific tasks (like calculations)
Sub-Agents (different pattern):

Agent A transfers control completely to Agent B
Agent B takes over and handles all future user input
Agent A is out of the loop
Use case: Handoff to specialists (like customer support tiers)
In our currency example: We want the currency agent to get calculation results and continue working with them, so we use Agent Tools, not sub-agents.

---
## Day 3 - Context Engineering: Sessions & Memory
* [Lab 3a](https://www.kaggle.com/code/kaggle5daysofai/day-3a-agent-sessions-sanyasyed): Agent Sessions
* [Lab 3b](https://www.kaggle.com/code/kaggle5daysofai/day-3b-agent-memory-sanyasyed): Agent Memory
* [White Paper- Context Engineering: Sessions & Memory](https://www.kaggle.com/whitepaper-context-engineering-sessions-and-memory) 
* [Podcast- Context Engineering: Sessions & Memory](https://www.youtube.com/watch?v=FMcExVE15a4)

### Notes
Types Of Knowledge Storage
1. Sessions - the container for a single, immediate conversation's history (Short Term Memory)
  * State:
    * session.state is the Agent's scratchpad, where it stores and updates dynamic details needed during the conversation.
    * Think of it as a global {key, value} pair storage which is available to all subagents and tools.
  * Events:
    * session.events are the building blocks of a conversation.
  * Service
    * SessionService: The storage layer
    * InMemorySessionService()
    * DatabaseSessionService() `session_service = DatabaseSessionService(db_url="sqlite:///my_agent_data.db")`
    * Agent Engine Sessions	- Production on GCP the cloud
  * Runner
    * The orchestration layer
    ``` python
    runner = Runner(
    agent=user_agent,
    app_name=APP_NAME,
    session_service=session_service,
    memory_service=memory_service,)
    ```
  * Context Compaction
      * this feature automatically reduce the context that's stored in the Session
      * assign Agent to App
      * `EventsCompactionConfig(compaction_interval=3, overlap_size=1,)`
        * `compaction_interval`: Asks the Runner to compact the history after every n conversations
        * `overlap_size`: Defines the number of previous conversations to retain for overlap
  ```
  Session = A notebook 📓
  Events = Individual entries in a single page 📝
  SessionService = The filing cabinet storing notebooks 🗄️
  Runner = The assistant managing the conversation 🤖
  ```
2. Memory - the long-term persistence mechanism
  * **Integration process** - 3 step:
    1. Initialize → Create a MemoryService and provide it to your agent via the Runner
       * ADK provides multiple `MemoryService` implementations through the `BaseMemoryService` interface:
        * `InMemoryMemoryService()` - Built-in service for prototyping and testing (keyword matching, no persistence)
        * `VertexAiMemoryBankService()` - Managed cloud service with LLM-powered consolidation and semantic search
        * Custom implementations - You can build your own using databases, though managed services are recommended
    1. Ingest → Transfer session data to memory using add_session_to_memory()
       1. `session_service.get_session()` : to get the session eg: `session = await session_service.get_session(app_name=APP_NAME, user_id=USER_ID, session_id="conversation-01")`
       * `add_session_to_memory()` - Use this function to make session information available for long-term recall. You explicitly transfer it to the memory using this function. eg: `await memory_service.add_session_to_memory(session)`
    1. Retrieve → Search stored memories using search_memory()
       * `load_memory()` - Agent decides when to search memory
       * `preload_memory()` - Automatically searches before every turn
  * **Manual Memory** Search - you can also search memories directly in your code.
  * **Automating Memory** Storage
    * Callbacks
      * `before_agent_callback` → Runs before agent starts processing a request
      * `after_agent_callback` → Runs after agent completes its turn
      * `before_tool_callback` / `after_tool_callback` → Around tool invocations
      * `before_model_callback` / `after_model_callback` → Around LLM calls
      * `on_model_error_callback` → When errors occur 
  * **Memory Consolidation** - Managed Memory Services handle consolidation automatically 

---

## Day 4 - Agent Quality
* [Lab 4a](https://www.kaggle.com/code/kaggle5daysofai/day-4a-agent-observability-sanyasyed): Agent Observability
* [Lab 4b](https://www.kaggle.com/code/kaggle5daysofai/day-4b-agent-evaluation-sanyasyed): Agent Evaluation
* [White Paper - Agent Quality](https://www.kaggle.com/whitepaper-agent-quality) 
* [Podcast- Agent Quality](https://www.youtube.com/watch?v=LFQRy-Ci-lk)

### Podcast Notes

#### **Core Themes**

* The “**LLM-as-a-Judge**” paradigm and the critical role of **Human-in-the-Loop (HITL)** evaluation.
* **Designing for quality, not just testing for it** → Agents must be *built* to be observable and evaluable from day one.
* Agent systems are **non-deterministic, dynamic, and evolving**, so old software testing models fail.

---

### **3 Core Messages of Agent Quality**

##### **1. Trajectory Is the Truth**

* Do not judge an agent only by its final output.
* You need the **entire chain of thought, planning steps, tool calls, and decisions** to understand quality & safety.
* A correct answer reached through a broken or inefficient path is still a quality issue.

##### **2. Observability Is Foundational**

To evaluate the trajectory, you must *see* it:

###### **Logging**

* Fine-grained, structured (JSON) logs.
* Capture internal reasoning, tool inputs/outputs, and step-by-step progression.

###### **Tracing**

* Connect logs into a **cause-and-effect narrative** (OpenTelemetry spans).
* Shows how each step led to the next; essential for debugging multi-step failures.

###### **Metrics**

* **System Metrics (for Ops/SRE)**

  * Latency (P50/P99), token cost, error rates, tool/API failures.
* **Quality Metrics (for Product/Data Science)**

  * Correctness, helpfulness, trajectory adherence, success rates by category.

##### **3. Evaluation Is a Continuous Loop**

* Called the **Agent Quality Flywheel**.
* Every real-world run—especially failures—feeds back into agent improvement.
* Continuous feedback → improved agent → stronger evaluation → better data → repeat.

---

### **Traditional Coding vs AI Agents**

* **Traditional software:** deterministic, explicit failure modes (delivery truck).
* **Agents:** dynamic decision-makers like **Formula 1 cars** → subtle, quiet failures, evolving behavior, unpredictable paths.

---

### **Agent Failure Modes**

* **Algorithmic Bias** – e.g., resume screening learns past discriminatory patterns.
* **Factual Hallucination** – confidently incorrect statements or invented facts/sources.
* **Performance & Concept Drift** – world changes but model doesn’t (fraud patterns, customer behavior).
* **Emergent Unintended Behaviors** – develops superstitions or exploits loopholes to achieve goals.

---

### **4 Pillars of Quality**

1. **Effectiveness** – Did it accomplish the real user goal? (not just task completion)
2. **Efficiency** – Latency, cost, path optimality; did it solve the problem well?
3. **Robustness** – Handles unclear instructions, API errors, edge cases gracefully.
4. **Safety & Alignment** – Ethics, guardrails, refusing harmful tasks, preventing prompt injection. *Non-negotiable.*

---

### **Evaluation Approaches**

#### **Outside-In Evaluation**

* Start with **end-to-end evaluation** (black box):

  * Did it succeed?
  * User satisfaction (CSAT).
* Shows **what** failed but not **why**.

#### **Inside-Out Evaluation (Trajectory Evaluation)**

* Inspect the **full reasoning path** for root causes:

  * Faulty planning (repetition, losing context).
  * Incorrect tool usage.
  * Misinterpreting tool/API responses.
* Crucial for diagnosis.

##### **Evil-Case Testing (Kaggle ADK)**

* Save a **successful trajectory** (tool calls + reasoning) as an *“eval case”*.
* Use it as a **regression test**: if the agent deviates, something broke.
* "Locks in the known good path."

---

### **Hybrid Evaluation System**

##### **1. Automated Metrics**

* ROUGE, BERTScore, etc.
* Quick surface-level similarity indicators.
* Useful for CI/CD trend monitoring, **not** for deep quality.

##### **2. LLM-as-a-Judge**

* A strong LLM evaluates the agent’s output.
* Use **pairwise comparison** instead of ratings (avoids central-tendency bias).
* Produces clear win/loss signal.

##### **3. Agent-as-a-Judge**

* A specialized agent that evaluates **another agent’s trajectory**.
* Judges reasoning steps, tool choices, decision quality.

##### **4. HITL (Human-in-the-Loop)**

* Humans set standards, judge nuance, create golden datasets.
* Essential for high-stakes tasks → interruption workflow (e.g., payment approval).
* Good reviewer UI:

  * Conversation on left
  * Trajectory (thoughts + tool calls) on right

---

### **Responsible AI (RAI) Layer**

* Continuous red-teaming to find vulnerabilities.
* Safety components implemented as **plugins**:

  * `before_model_callback` – input scanning (prompt injection).
  * `after_model_callback` – output scanning (PII leaks, policy violations).

---

### **Dynamic Sampling**

* Full tracing of **100% of failures**.
* Lower sampling (e.g., 10%) for successful runs.
* Balances performance with visibility.

---

### **The Agent Quality Flywheel (Summary)**

1. **Define** quality goals (pillars).
2. **Instrument** for observability (logs, traces, metrics).
3. **Evaluate** continuously (hybrid system).
4. **Improve** agents using real-world insights.
5. **Repeat** → agents become more reliable, safe, and aligned.

---

### **3 Absolute Takeaways**

1. **Evaluation must be designed in.**
   It’s an architectural pillar, not a late-stage QA task.

2. **Trajectory is the truth.**
   The real story of quality is in the reasoning path, not the final output.

3. **Humans remain the arbiters of quality.**
   Automation scales, but humans define correctness, safety, and nuance.

---

## Day 5 - Agent Tools & Interoperability with Model Context Protocol (MCP)
* [Lab 5a](https://www.kaggle.com/code/sanyasyed/day-2a-agent-tools-sanyasyed): Agent Tools
* [Lab 5b](https://www.kaggle.com/code/sanyasyed/day-2b-agent-tools-best-practices-sanyasyed): Agent Tools Best Practices
* [White Paper- Agent Tools & Interoperability with MCP](https://www.kaggle.com/whitepaper-agent-tools-and-interoperability-with-mcp) 
* [Agent Tools & Interoperability with MCP Podcast](https://www.youtube.com/watch?v=Cr4NA6rxHAM)

### Podcast Notes - Deploying, Scaling & Productionizing AI Agents*
Here are clean, organized, **GitHub-ready notes** based on the full podcast transcript.
I’ve written them in **markdown style** so you can paste them directly into your repo’s README or a `/notes/whitepaper.md` file.

If you want these in a canvas or as a file, just let me know.

---

##### 🎯 Overview

Modern AI agents are easy to prototype but *hard* to productionize. The “last-mile gap” is huge—over **80% of real engineering effort** goes not into the AI model, but into infrastructure, validation, safety, and tooling. This white paper outlines how to move from a clever agent demo to a reliable enterprise-grade system.

---

#### 1. Why AI Agents Need New Operational Thinking

AI agents **behave dynamically**—they reason, choose tools, interact, and maintain memory.
Traditional MLOps falls short because:

* Agents don’t follow deterministic paths
* They may never take the same execution path twice
* They orchestrate tools on the fly
* They require scalable, secure state/memory management
* Their cost and latency are unpredictable

Thus, “AgentOps” is the emerging discipline.

---

#### 2. Key Pillars of Agent Production Systems

The white paper breaks it down into three foundational pillars:

##### **1. Automated Evaluation**

Evaluate both **outputs** and **behaviors**, e.g.:

* Tool choice and correctness
* Reasoning quality
* Memory usage
* Safety and hallucination checks

##### **2. Automated Deployment (CI/CD)**

Use evaluation-gated deployment to prevent bad agents from reaching users.

##### **3. Observability**

Full visibility through:

* Logs
* Traces
* Metrics

---

### 3. People & Roles Needed

Before tooling—fix the team structure.

##### ⚙️ Existing roles

* Cloud/platform engineering
* Security
* Traditional MLOps

##### ⭐ New roles for GenAI

###### **Prompt Engineer**

* Defines system instructions (“agent constitution”)
* Enforces domain-specific guardrails
* Designs prompt structures and evaluation datasets

###### **AI Engineer**

* Builds backend systems integrating:

  * Guardrails
  * RAG
  * Tools
  * Memory
  * Automated evaluation pipelines

Close collaboration across all teams is mandatory.

---

### 4. Pre-Production: Evaluation-Gated CI/CD

This is the core engine.

#### 📌 Phase 1: Pre-merge CI

Fast checks before code hits `main`:

* Unit tests
* Linting & style checks
* Quick security scans
* Core agent evaluation suite

Goal: *Fast feedback, clean main branch.*

#### 📌 Phase 2: Post-merge → Staging

Heavy testing in a production-like environment:

* Load testing
* Integration testing with external services
* Internal user testing (“dogfooding”)

#### 📌 Phase 3: Gated Production Deployment

* Release must be the exact validated build artifact
* Typically requires human approval
* Backed by infrastructure-as-code (e.g., Terraform)

---

### 5. Safe Rollout Strategies

To reduce risk in production:

* **Canary releases** (1% users first)
* **Blue/Green deployments** (switch traffic instantly)
* **A/B testing** (compare agent variants on real metrics)
* **Strict versioning** of

  * Code
  * Prompts
  * Tool schemas
  * Memory structures

Versioning = instant rollback ability.

---

### 6. Security: The SIF Framework

Google’s 3-layer secure AI agent model:

##### **Layer 1 — Policy Definition**

System instructions define “constitutional rules.”

##### **Layer 2 — Guardrails & Filtering**

* Input filtering (e.g., Perspective API)
* Output filtering (PII, hate speech, safety)
* Human-in-the-loop (HITL) gating for high-risk actions

##### **Layer 3 — Continuous Assurance**

* Continuous safety testing
* Responsible AI evaluations
* Red teaming (simulated attacks)

Threats include:

* Prompt injection
* Data leakage
* Memory poisoning

---

### 7. Operations: Observe → Act → Evolve

Agents need continuous management—not deploy-and-forget.

#### 🔍 1. Observe (Building the “Sensory System”)

* **Logs** → detailed events
* **Traces** → causal chains across services
* **Metrics** → latency, error rate, tool success rate, cost/user, satisfaction

#### 🛠 2. Act (Control & Stability)

Key design principles:

* **Decouple state from logic**

  * Use external memory stores (like Cloud SQL)
* **Idempotent tools**

  * Safe retries with exponential backoff
* **Cost controls**

  * Caching
  * Prompt optimization
  * Batch requests

##### Security Incident Response (Playbook)

1. **Contain** (disable risky tools via feature flags)
2. **Triage** (route to HITL)
3. **Investigate**
4. **Resolve & redeploy** using CI/CD

#### 🚀 3. Evolve (Continuous Improvement)

* Convert real production failures → new “golden dataset” test cases
* Iterate prompts, guardrails, tools
* Deploy upgrades in hours, not weeks

---

### 8. Multi-Agent Systems & Interoperability

Organizations will have many specialized agents. To avoid silos, two protocols matter:

#### 🧰 **MCP — Model Context Protocol**

* Stateless
* For interacting with tools and static resources
* Example: “Fetch current weather for London”

#### 🤝 **A2A — Agent-to-Agent Protocol**

* Stateful
* For collaboration or delegating goals
* Example: “Analyze churn and propose retention strategies”

##### Analogy

* Supervisor agent uses **A2A** to delegate to mechanic agent
* Mechanic uses **MCP** to call diagnostic tools

##### Agent Discovery

Uses **agent cards** (JSON descriptors):

* Capabilities
* URLs
* Skills
* Authentication requirements

##### Infrastructure Requirements

* Distributed tracing across agents
* Shared registries for large orgs
* Robust state management

---

### ⭐ High-Level Takeaways

* Prototyping agents is easy; **productionizing** them is hard.
* **80%** of effort is in systems, not AI.
* Evaluation-gated CI/CD is the backbone.
* Observability and versioning are non-negotiable.
* Multi-agent collaboration requires standards (A2A, MCP).
* Security requires layered, continuous defenses.
* Production agents are *living systems* that must evolve daily.
---


