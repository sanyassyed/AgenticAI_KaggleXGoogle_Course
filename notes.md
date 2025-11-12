# 5 Day Course Notes
## Day 1 - Introduction to AI Agents
* [Lab 1a](https://www.kaggle.com/code/sanyasyed/day-1a-from-prompt-to-action-sanyasyed): From Prompt to Action
* [Lab 1b](https://www.kaggle.com/code/sanyasyed/day-1b-agent-architectures-sanyasyed): Agent Architecture
* [White Paper- Introduction to Agents](https://www.kaggle.com/whitepaper-introduction-to-agents)
* [Introduction to Agents Podcast](https://www.youtube.com/watch?v=zTxvGzpfF-g)
  
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

### 💬 Key Terminologies

* **Interoperability:** The ability of different systems and applications to communicate and work together effectively.
* **MCP (Model Context Protocol)** — open standard for connecting AI to external systems
* **Agent Development Kit (ADK)** - a flexible and modular framework for developing and deploying AI agents

---

## Day 2 - Agent Tools & Interoperability with Model Context Protocol (MCP)
* [Lab 2a](https://www.kaggle.com/code/sanyasyed/day-2a-agent-tools-sanyasyed): Agent Tools
* [Lab 2b](https://www.kaggle.com/code/sanyasyed/day-2b-agent-tools-best-practices-sanyasyed): Agent Tools Best Practices
* [White Paper- Agent Tools & Interoperability with MCP](https://www.kaggle.com/whitepaper-agent-tools-and-interoperability-with-mcp) 
* [Agent Tools & Interoperability with MCP Podcast](https://www.youtube.com/watch?v=Cr4NA6rxHAM)
  
### Introduction: Models, Tools and Agents 
* Tools become the eyes and hands of the foundation models
Tools and tool calling 8
What do we mean by a tool? 8
Types of tools 10
Built-in tools 11
Agent Tools 13
Best Practices 15
Documentation is important 15
Describe actions, not implementations 17
Publish tasks, not API calls 18
Make tools as granular as possible 18
Design for concise output 19
Use validation effectively 19
Understanding the Model Context Protocol 20
The "N x M" Integration Problem and the need for Standardization 20
Table of contents

Core Architectural Components: Hosts, Clients, and Servers 21
The Communication Layer: JSON-RPC, Transports, and Message Types 22
Key Primitives: Tools and others 24
Tool Definition 26
Tool Results 28
Structured Content 29
Error Handling 29
Other Capabilities 31
Resources 31
Prompts 31
Sampling 32
Elicitation 33
Roots 33
Model Context Protocol: For and Against 34
Capabilities and Strategic Advantages 34
Accelerating Development and Fostering a Reusable Ecosystem 34
Table of contents

Architectural Flexibility and Future-Proofing 35
Foundations for Governance and Control 36
Critical Risks and Challenges 36
Enterprise Readiness Gaps 38
Security in MCP 39
New threat landscape 39
Risks and Mitigations 40
Tool Shadowing 42
Malicious Tool Definitions and Consumed Contents 44
Sensitive information Leaks 45
No support for limiting the scope of access 46
Conclusion 48
Appendix 49
Confused Deputy problem 49
The Scenario: A Corporate Code Repository 49
The Attack 50

