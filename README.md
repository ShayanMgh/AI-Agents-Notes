# 🤖 AgenticAI Course Recap – Ed Donner

## 🎓 **Course Overview: Building AI Agents**

This course teaches engineering AI agents through a structured, hands-on curriculum across **6 weeks**. Each week builds upon the last, blending **theory**, **frameworks**, and **practical projects**.

---

## 📚 **What You’ll Learn**

### 🧠 Week-by-Week Breakdown

#### **Week 1: Foundations**
- Understand **agentic architectures**
- Use **LLMs** to build basic agents without frameworks
- **Final project**: Personal career agent for your website

#### **Week 2: OpenAI Agents SDK**
- Learn the OpenAI Agents SDK
- Implement **guardrails**
- Build the **Deep Research** app

#### **Week 3: CrewAI**
- Low-code tool to configure **agent teams**
- Multiple projects to explore use cases

#### **Week 4: LangGraph**
- Full-code, **powerful and complex** framework
- Tackle **advanced workflows**

#### **Week 5: Microsoft Autogen**
- **Agent collaboration** environment
- Explore modular ecosystem

#### **Week 6: Capstone & MCP (Model Context Protocol)**
- Learn about **MCP** from Anthropic — for **multi-model collaboration**
- **Final capstone**: Ties all learnings together

---

## 💡 **Major Projects**

Projects grow in complexity over time:

1. Career Agent (Week 1)
2. Deep Research App (Week 2)
3. Multi-agent collaborations (CrewAI)
4. LangGraph applications
5. **Engineering Team Simulation**: Agents simulate dev roles
6. **Sidekick Agent**: Local browser-based assistant
7. **Creator Agent**: Agents that build other agents
8. **Trading Simulation**: Agents analyze news & simulate trades

---

## 🎯 **Course Goals**

- **Educational**: Master agent development concepts & skills  
- **Commercial**: Apply learnings in real-world **B2B/B2C** settings

---

## 🧱 **What Are Agentic AI Frameworks?**

Frameworks **simplify AI agent development** by abstracting:
- Prompt orchestration
- Tool use
- System glue logic

> 💡 Goal: Let developers focus on solving problems, not wiring systems.

---

## ⚙️ **Framework Landscape (by Complexity)**

### 🟢 **1. No Framework / Minimal Abstraction**
- Direct API calls to LLMs
- Full control over prompts & logic
- Manual but transparent
- Recommended by **Anthropic**

#### ➡️ **MCP (Model Context Protocol)**
- Not a framework, but a **protocol** by Anthropic
- Enables **plug-and-play** across models, tools, and data
- Open-source, standard-based, minimal glue code

---

### 🟡 **2. Lightweight Frameworks**

#### 🔹 **OpenAI Agents SDK**
- Clean, new, and developer-friendly
- Ideal for small teams and fast prototyping

#### 🔹 **CrewAI**
- Collaborative multi-agent systems
- **Low-code** (YAML config)
- Slightly more complex than OpenAI SDK

---

### 🔴 **3. Heavyweight Frameworks**

#### 🔸 **LangGraph (LangChain team)**
- Build agents as **computational graphs**
- High flexibility for complex workflows
- Steep learning curve

#### 🔸 **AutoGen (Microsoft)**
- Best for **structured multi-agent conversations**
- Modular, versatile, requires conceptual investment

---

## 📌 **How to Choose a Framework**

Depends on:
- Complexity of your use case
- Need for state/collaboration
- Developer skill set
- Preference: control 🆚 abstraction

> 🧑‍🏫 Instructor prefers **lightweight tools** that stay out of your way, while acknowledging power of heavyweight options.

---

## 🧠 **Resources**

Definition: Extra context injected into prompts to make an LLM smarter

### ✅ Key Ideas:
- **Basic**: Manually insert data into prompts  
- **Smarter**: Use **RAG (Retrieval-Augmented Generation)** to fetch only relevant info

### Example:
Provide ticket pricing data to a travel assistant LLM so it can answer questions.

---

## 🛠️ **Tools**

Definition: Capabilities the LLM can **use to act**, like querying APIs or sending messages.

> 🎯 Goal: Give the LLM **autonomy** to act, not just respond.

### 🔍 How It Works (Under the Hood)
```json
Prompt: “You can use 'fetch_ticket_price'. If needed, reply with JSON.”
User: “I want to fly to Paris.”
LLM: { "tool": "fetch_ticket_price", "destination": "Paris" }
```
## 🔄 **Tools vs. Resources**

| **Feature**   | **Resources**                  | **Tools**                          |
|---------------|--------------------------------|------------------------------------|
| **Role**      | Provide information            | Execute actions                    |
| **How Used**  | Injected into prompt           | Structured responses from LLM      |
| **Autonomy**  | Low–Medium (assistive)         | High (autonomous behavior)         |




