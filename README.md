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


# 🚀 Week 2: Asyncio & OpenAI Agents SDK

---

## ⚡ **Why Learn Asyncio?**

- Async Python is foundational across all major agent frameworks (**OpenAI SDK, CrewAI, LangGraph**, etc.).
- It enables agents to handle many concurrent tasks efficiently — especially I/O-bound operations like:
  - Waiting on LLM responses
  - Fetching web data
  - Querying databases or tools

---

## 🧵 **What Is Asyncio?**

- A **lightweight concurrency model** in Python (since 3.5)
- NOT multithreading or multiprocessing — avoids OS-level threads
- Runs a **single-threaded event loop** that switches between tasks while they wait

---

## 🔑 **Core Concepts**

### ✅ `async def`
- Declares a **coroutine** (not a regular function)
- Returns a coroutine object — doesn’t execute immediately

### ✅ `await`
- Pauses execution and **waits for a coroutine** to finish

```python
async def fetch_data():
    return "done"

result = await fetch_data()
```
✅ **Coroutine**
- A function that can **pause and resume**
- Scheduled and managed by Python’s **event loop**

---

🌀 **The Event Loop**

The engine that powers asyncio:

- Starts and pauses coroutines
- Runs other coroutines while one is waiting
- Enables concurrent behavior in I/O-heavy programs

### 🛠️ Useful Pattern: `asyncio.gather()`

- Run multiple coroutines concurrently.

```python
results = await asyncio.gather(
    fetch_data1(),
    fetch_data2(),
    fetch_data3()
)
```
Efficient when calling multiple APIs or agents at once.

### 🧠 How to Think About It

- Async Python = manual multitasking at the code level.
- Great for multi-agent orchestration, background tasks, and responsiveness.

---

### 📌 Bottom Line

| Concept          | Meaning                                  |
|------------------|-------------------------------------------|
| `async def`      | Define a coroutine                        |
| `await`          | Run the coroutine and wait for result     |
| Coroutine        | Pauseable, resumable function             |
| Event loop       | Orchestrates coroutine execution          |
| `asyncio.gather` | Run multiple coroutines concurrently      |

---

### 🚀 OpenAI Agents SDK: Overview

- Lightweight, flexible, and not opinionated — lets you design agents your way.
- Simplifies common tasks like tool use and LLM orchestration (e.g., managing JSON, if-statements).
- Great for rapid prototyping without getting bogged down in boilerplate.

---

### ⚙️ Why Use It?

- Handles routine complexity like:
  - Tool invocation structure
  - Multi-step agent coordination
  - Prompt formatting & response parsing
- Makes tool usage clean and maintainable without losing control over the logic.

---

### 📚 Key Terminology

| Term       | Meaning                                             |
|------------|------------------------------------------------------|
| Agent      | A defined role + behavior built around LLM calls     |
| Handoff    | Interaction or communication between agents          |
| Guardrails | Checks and constraints to keep agents on-task & safe |

---

### 🧪 How to Use It: The 3-Step Pattern

1. **Create an agent instance**  
   → Define what role the agent plays (e.g., researcher, planner, responder).

2. **Use with `trace` block**  
   → Optional but recommended for debugging and logging interactions using OpenAI’s trace viewer.

3. **Run the agent with `runner.run()`**  
   → This is a coroutine → must use `await`.

---

### 🔁 Typical Code Flow

```python
async def main():
    agent = Agent(role=..., instructions=...)
    with trace(agent):
        result = await runner.run(agent)
```
### 🎧 What Is Vibe Coding?

Coined by **Andrej Karpathy**, **vibe coding** is a relaxed, iterative way of coding with LLMs — generating snippets, tweaking them, and building up functionality quickly without overplanning.

---

### ✅ Why It’s Powerful

- Boosts creativity and momentum.
- Lets you explore and learn new frameworks or APIs quickly.
- Perfect for prototyping and experimenting.

---

### 🛡️ 5 Survival Tips for Effective Vibe Coding

#### 1. Good Vibes
- Craft high-quality prompts you can reuse.
- Ask for concise, modern code (LLMs can be verbose or outdated).
- Include today’s date to get up-to-date API usage.

#### 2. Vibe but Verify
- Don’t trust one model blindly.
- Cross-check outputs by asking the same question to multiple LLMs (e.g., ChatGPT & Claude).

#### 3. Step Up the Vibe
- Avoid giant blobs of LLM-generated code.
- Ask for code in small, testable chunks (e.g., one function at a time).
- Not sure how to break it down? Ask the LLM to design the step-by-step breakdown first.

#### 4. Vibe and Validate
- Use a second LLM to review or optimize what the first LLM wrote.
- Ask for feedback: _“Is this the cleanest/best way to do it?”_
- Emulates the evaluator-optimizer agent pattern manually.

#### 5. Vibe with Variety
- Ask for multiple solutions to the same problem.
- Encourage creativity and comparison.
- Request explanations to deepen your understanding and catch flaws.

---

### 💬 Final Thought

> Vibe coding is fun only if you understand what's going on.  
> Always follow up by asking the LLM to explain the code until it’s fully clear to you.  
> Otherwise, debugging becomes painful fast.
