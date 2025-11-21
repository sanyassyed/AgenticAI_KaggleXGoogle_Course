# **Day 1 – Introduction to AI Agents 🧠**

## 🔗 Labs & Resources

* **Lab 1a:** From Prompt to Action
* **Lab 1b:** Agent Architecture
* **White Paper:** Introduction to Agents
* **Podcast:** Introduction to Agents

---

## 🧩 Core Components

| **Component**                   | **Role**       | **Description**                                             |
| ------------------------------- | -------------- | ----------------------------------------------------------- |
| **Model (Brain / Reasoning)**   | LLM            | Thinks, plans, decides next steps based on context + memory |
| **Tools (Hands)**               | APIs, DBs, Web | Extend capability to access or act in the world             |
| **Orchestration (Coordinator)** | Manages flow   | Controls tool calls, feedback loops, decision flow          |

---

## ⚙️ ReACT Framework

### What It Means

**ReACT = Reason + Act** through iterative steps.

### 🔄 Cycle

1. **Think** – plan a step
2. **Act** – call a tool
3. **Observe** – read results
4. **Repeat** – continue until goal is complete

---

## 📏 Key Metrics

* **Security**
* **Quality**
* **Reliability**

---

## 🧠 System Concepts

1. **Anatomy** – Model + Tools + Orchestration
2. **Taxonomy** – Simple → multi-agent
3. **Architectural Design** – How components interact
4. **Productionization** – Secure + scalable + observable

Lifecycle: **Build → Deploy → Manage**

---

## 🧭 Agentic Systems

Agents plan, act, and reason using tools.
Tool outputs are appended back into the system prompt.

---

## 🔁 5-Step Operational Loop

1. Get the Mission
2. Scan the Scene
3. Think it Through
4. Take Action
5. Observe & Iterate

---

## 🧮 Taxonomy of Agentic Systems

| Level | Description              | Notes                 | Example                |
| ----: | ------------------------ | --------------------- | ---------------------- |
| **0** | Core Reasoning           | No tools              | Pure LLM reasoning     |
| **1** | Connected Problem Solver | RAG / APIs            | Get current weather    |
| **2** | Strategic Solver         | Heavy context         | Compare coffee shops   |
| **3** | Multi-Agent System       | Manager + specialists | Project manager agent  |
| **4** | *Future*                 | Self-evolving         | Autonomous improvement |

---

## 🏗️ Architectural Design

### 🧩 Model

* Superior reasoning
* Reliable tool use
* Optimized for speed/quality/cost

**Model routing:** choose the right model per task.

### 🧰 Tools (Retrieval + Action)

#### 🔍 Retrieval Tools

* RAG
* NL-to-SQL

#### ⚙️ Action Tools

* APIs
* HITL (Human-in-the-Loop)

#### 🛠️ Function Calling

* Via **MCP (Model Context Protocol)**
* Implemented through **ADK (Agent Development Kit)**

---

## 🕸️ Orchestration Layer

### 🧭 Core Choices

* Domain knowledge
* Persona
* Context augmentation

### 🧠 Memory Types

| Type           | Description                      |
| -------------- | -------------------------------- |
| **Short-term** | Scratchpad / immediate reasoning |
| **Long-term**  | Vector DB / persistent knowledge |

### 🤝 Multi-Agent Pattern

**Coordinator Pattern**

* Manager agent = delegator
* Specialist agents = domain experts

---

## 🧪 Testing & Debugging

### FMOps

* Manage large models
* Versioning + deployment

### AgentOps

* Evaluate reasoning + tool quality
* Telemetry + benchmarks

---

## 💬 Key Terminologies

* **Interoperability:** systems working together
* **MCP:** protocol to connect models to tools
* **ADK:** framework for building agents

---

# **Day 2 – Agent Tools & MCP 🔧**

## 🔗 Labs & Resources

* Lab 2a: Agent Tools
* Lab 2b: Best Practices
* White Paper
* Podcast

---

## 🧰 Agent Tools vs Sub-Agents

### 🔨 Agent Tools (What we use)

* Agent A **calls** Agent B as a tool
* Agent A **remains in control**

### 🧑‍🏫 Sub-Agents (Different pattern)

* Agent A **hands over** the conversation
* Agent B takes full control

### 💡 Example

Currency conversion → use **agent tools**, not sub-agent delegation.

---

# **Day 3 – Context Engineering: Sessions & Memory 🗂️**

## 🔗 Labs & Resources

* Lab 3a: Sessions
* Lab 3b: Memory
* White Paper
* Podcast

---

## 🧠 Types of Knowledge Storage

# 1️⃣ Sessions – Short-Term Memory

### 🧩 Components

* **State:** agent scratchpad
* **Events:** steps in conversation
* **SessionService:** storage backend
* **Runner:** orchestrates execution

### ✂️ Context Compaction

Automatically trims session history for efficiency.

---

# 2️⃣ Memory – Long-Term Storage

### 🧱 Integration Steps

1. **Initialize** memory service
2. **Ingest** session → memory
3. **Retrieve** when needed

### 🤖 Automation

Callbacks: before/after agent, tool, model steps.

### 🧬 Memory Consolidation

Managed services (Vertex memory) handle merging.

---

# **Day 4 – Agent Quality 📊**

## 🔗 Labs & Resources

* Lab 4a: Observability
* Lab 4b: Evaluation
* White Paper
* Podcast

---

## 🎙️ Podcast Themes

* LLM-as-a-Judge
* Human-in-the-loop
* Agents = dynamic, non-deterministic systems

---

## 🎯 3 Core Messages

### 1. Trajectory Is the Truth

Full reasoning path matters.

### 2. Observability Is Foundational

* Logs
* Traces
* Metrics

### 3. Evaluation Is Continuous

Real runs → insights → improvement loop.

---

## ⚠️ Agent Failure Modes

* Bias
* Hallucination
* Performance drift
* Emergent misbehavior

---

## 🧱 4 Pillars of Quality

1. Effectiveness
2. Efficiency
3. Robustness
4. Safety & Alignment

---

## 🧪 Evaluation Approaches

### Outside-In

End-to-end evaluation.

### Inside-Out

Evaluate reasoning path.

### Evil-Case Testing

Save good trajectories as regression tests.

---

## 🧰 Hybrid Evaluation

* Automated metrics
* LLM-as-judge
* Agent-as-judge
* HITL

---

## 🛡️ Responsible AI Layer

* Filtering
* Callbacks
* Safety plugins

---

# **Day 5 – Deploying, Scaling & Productionizing Agents 🚀**

## 🔗 Labs & Resources

* Lab 5a & 5b
* White Paper
* Podcast

---

## 🎯 Overview

Prototyping is easy; productionizing is hard.
**80%** of the real effort = infra, safety, evaluation.

---

## 🏛️ Pillars of Production

1. Automated evaluation
2. CI/CD deployment
3. Observability

---

## 👥 Roles Needed

* Cloud/platform
* Security
* MLOps

### New Roles

* **Prompt Engineer**
* **AI Engineer**

---

## 🔄 Pre-Production CI/CD

* Pre-merge checks
* Staging tests
* Gated production deployment

---

## 🛫 Release Strategies

* Canary
* Blue/Green
* A/B tests
* Versioning everything

---

## 🔐 Security – SIF Framework

1. Policy
2. Guardrails
3. Continuous Assurance

---

## 👁️ Operations

### Observe

Logs, traces, metrics

### Act

Feature flags, cost controls, retries

### Evolve

Failures → golden test cases

---

## 🤝 Multi-Agent & Interoperability

### MCP

Tool access

### A2A

Agent collaboration

---
