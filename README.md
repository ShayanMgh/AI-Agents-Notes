# 🤖 Agentic AI Engineering Course Recap – Ed Donner

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


# 🚀 Week 3 : Crew AI


---
### 🌐 What Is Crew AI?

Crew AI refers to **three distinct offerings**:

1. **Crew AI Enterprise** – A commercial platform for deploying, running, and managing agents (with UI dashboards).  
2. **Crew AI UI Studio** – A low-code/no-code tool for building agent workflows (similar to Addendum).  
3. **Crew AI Framework** – An open-source Python framework to orchestrate agent teams.  
   💡 _This is what the course focuses on._

---

### 🧠 Key Framework Concepts

#### 1. Crew vs Flows

- **Crew** = A team of agents collaborating autonomously.  
- **Flows** = Structured, rule-based workflows with precise steps.  
  - Use **Crew** for: creative, open-ended, autonomous collaboration.  
  - Use **Flows** for: auditability, control, deterministic logic.  

👉 _This course focuses on **Crews** because it's all about agent autonomy and collaboration._

---

### ⚖️ Comparison to OpenAI Agents SDK

- Crew has different constructs and terminology, but many shared ideas.  
- You’ll need to adapt mentally to the new structure, but it’s worth it.  
- Like OpenAI’s SDK, **Crew AI is also**:
  - ✅ Flexible  
  - ✅ Well-suited for multi-agent orchestration  
  - ✅ Increasingly popular  

---

### 🏁 Big Picture Insight

Each framework has strengths. As you explore more (e.g., Crew, Autogen, etc.), notice:

- What’s **similar**  
- What’s **better**  
- What **fits your project needs best**

---

## 🧱 Crew AI – Core Concepts & Structure

### 🧑‍🚀 1. Agent

- Smallest autonomous unit; wraps around an LLM.  
- Has:
  - **Role** – its function in the crew  
  - **Goal** – its purpose  
  - **Backstory** – context to improve behavior  
  - Optional: **memory** & **tools**

🆚 Compared to OpenAI SDK: _More prescriptive_ (vs. just using “instructions”).

---

### 📋 2. Task

- A specific assignment for an agent.  
- Has:
  - **Description**
  - **Expected Output**
  - **Assigned Agent**

✅ _New concept not present in OpenAI SDK._

---

### 👥 3. Crew

- A team of agents and tasks.  
- Two execution modes:
  - **Sequential**: tasks run one after the other.  
  - **Hierarchical**: a manager LLM assigns tasks dynamically.

---

### ⚙️ Structure & Implementation

#### 📁 Config (YAML) Files

- Used to define agents and tasks separately from code.  
- **Benefits**:
  - Cleaner codebase  
  - Easier editing/testing of prompts  
  - YAML is human-readable  

_Example:_  
```python
agent = Agent(config="researcher")
```
### 🐍 `crew.py` File

**Defines:**

- **Agents** → with `@agent` decorator  
- **Tasks** → with `@task` decorator  
- **Crew** → with `@crew` and `@crew_base` decorators  

> The `@agent` decorator registers agents for use in `self.agents`, and similarly for tasks.

---

### 🔁 Trade-Offs

**✅ Pros:**
- Encourages best practices in prompting (role, goal, backstory)
- YAML config promotes clean separation of concerns
- Hierarchical mode supports more dynamic workflows

**⚠️ Cons:**
- More opinionated and rigid than OpenAI SDK
- Less direct control over system prompts unless you dig deeper

---

### ⚙️ Crew AI – Model Access & Project Structure

#### 🔌 Flexible LLM Integration with LiteLLM

- Crew uses **LiteLLM** under the hood to connect to any LLM provider
- Lightweight, simple, and more flexible than LangChain

**Model format:**

```plaintext
"provider_name/model_name"
```

**Examples:**
- `"openai/gpt-4"`
- `"anthropic/claude-3"`
- `"google/gemini"`
- `"openrouter/meta-llama-3"`
- `"ollama/local-model"` (with a base URL)

> ✅ **Advantage over OpenAI SDK:** Easy switching across models and providers.

---

### 🧱 Crew Project Structure

To create a new agent project:

```bash
crewai create crew my_crew
```

**Project scaffold:**

```plaintext
my_crew/
├── src/
│   └── my_crew/
│       ├── config/
│       │   ├── agents.yaml     ← Agent definitions
│       │   └── tasks.yaml      ← Task definitions
│       ├── crew.py             ← Defines agents, tasks & crew (with decorators)
│       └── main.py             ← Entry point to run the crew
├── pyproject.toml              ← Project config (UV managed)
└── other uv-related files
```

---

### 🛠 Define Agents & Tasks in YAML

- Located in `config/` folder  
- Keeps prompts/config clean and separate

---

### 🧠 Implement Logic in `crew.py`

- Use decorators: `@agent`, `@task`, `@crew`
- Reference YAML or manually create agent/task instances

---

### 🚀 Configure `main.py`

- Pass runtime parameters (e.g., topic of a task)
- Call the crew object and run the workflow

---

### ▶️ Run the Project

```bash
crewai run
```

---

### 🏗️ Key Files

- `agents.yaml` / `tasks.yaml` → YAML configs (role, goal, LLM, etc.)
- `crew.py` → Decorator-based Python code to define crew logic
- `main.py` → Execution script
- `crewai run` → Runs the crew by executing `main.py`

---

### 📌 Summary of Benefits

- ⚡ Fast LLM switching via LiteLLM  
- 📁 Clean codebase with YAML + Python separation  
- 🧱 Structured projects support scalability and clarity  
- 🧰 Uses `uv` for project management (integrates well with your course setup)

---

### 🧰 New Concepts Introduced

#### 🛠 Tools
- Equip agents with external capabilities  
- Similar to tools in OpenAI SDK

#### 🔄 Context Passing
- Explicit way to pass outputs from one task to another  
- Crucial for multi-step logic or sequential tasks

---

### 🔍 Extra: Using Serper API

- A lightweight Google Search API for agent tools  
- Free with 2500 credits

**Add key to `.env`:**

```env
SERPER_API_KEY=your_key_here
```

> 📝 Note: not the same as SerpAPI — use [serper.dev](https://serper.dev)

---

### 🧠 Memory in Crew AI

Crew supports **5 memory types** — focus on these 3:

---

#### 1. **Short-Term Memory**
- Uses vector database (e.g., Chroma)  
- Ideal for related task context passing  
- Uses **RAG** (retrieval augmented generation)

---

#### 2. **Long-Term Memory**
- Stores persistent info with **SQLite**  
- Builds knowledge across long timelines

---

#### 3. **Entity Memory**
- Like short-term, but tracks named entities (people, places, concepts)  
- Vector-based storage

---

**Additional Types:**
- **Contextual Memory** – Umbrella term combining short/long/entity  
- **User Memory** – For user-specific info (manual handling required)

  
# 🚀 Week 4 : LangChain and LangGraph


---
🧠 Context: LangChain Ecosystem Overview
1. LangChain  
* Originally built to abstract away LLM-specific integration complexities.  
* Focused on chaining LLM calls, tool use, memory, RAG, prompt templates.  
* Powerful, but:  
    * Opinionated.  
    * Less transparent (abstracts away prompt logic).  
    * Less necessary now that LLM APIs are standardized (especially OpenAI-style).  

2. LangGraph  
* Not part of LangChain per se (though from same company).  
* Focus: stable, scalable, fault-tolerant workflows for agent systems.  
* Think of it as a graph of nodes, where each node is:  
    * An agent  
    * A logic step  
    * A human-in-the-loop  
    * A memory checkpoint  
📌 Core Idea: Model complex workflows as graphs to enable control, repeatability, and fault tolerance.  
Key Features:  
    * Human-in-the-loop support  
    * Memory handling (via LangChain or external)  
    * "Time travel": checkpointing and rewinding to prior graph state  
    * Robust retry & fallback  
    * Plug-and-play: you can use LangChain or not  

3. LangSmith  
* Separate product for debugging, visibility, and analytics  
* Can be used with:  
    * LangChain  
    * LangGraph  
    * Standalone LLM apps  
* Tracks inputs, outputs, reasoning paths  
* Useful for monitoring and debugging your agent workflows  

⚙️ Why Use LangGraph?  
**Need** | **Solution LangGraph Offers**  
---|---  
Complex agent collaboration | Graph-based workflow control  
Fail-safety & retries | Fault tolerance built-in  
Workflow versioning/checkpoints | “Time travel” to restore previous states  
Inter-agent communication | Modeled through graph edges  
Monitoring | Via LangSmith integration  

🧭 Summary  
* LangChain = abstraction framework for LLM apps (with memory, RAG, tools, etc.)  
* LangGraph = graph-based framework for building resilient multi-agent systems  
* LangSmith = monitoring/debugging tool for both  

📦 LangGraph = 3 Distinct Parts  
**Component** | **Purpose**  
---|---  
LangGraph (Framework) | Open-source core used to build agent workflows (like Crew’s framework).  
LangGraph Studio | Visual builder to design graphs via UI (similar to Crew Studio).  
LangGraph Platform | Hosted enterprise service to deploy/run LangGraph apps (like Crew Enterprise).  
⚠️ Note: The website promotes LangGraph Platform heavily — likely the commercial focus.  

🧠 Anthropic’s Perspective on Frameworks  
From their blog “Building Effective Agents”:  
* Frameworks like LangGraph help by abstracting:  
    * LLM calls  
    * Tool usage  
    * Chaining logic  
* But:  
    * Abstractions can hide the real prompts and make debugging harder.  
    * Encourage unnecessary complexity when simple code would do.  
Their recommendation:  
🔹 Start with direct LLM API use (simple JSON, raw calls).  
🔹 Use frameworks only if you understand what they abstract.  
🔹 Incorrect assumptions about frameworks often lead to errors.  

🧭 Summary Takeaway  
**LangGraph Strengths** | **Anthropic’s Caution**  
---|---  
Stability, resilience, checkpointing via graph | Adds complexity and hides prompt details  
Ideal for large, multi-agent workflows | May not be needed for small/simple applications  
Visual tools and hosted platform | Prefer lightweight, transparent implementations  

🧠 Core Concepts in Landgraf  
**Term** | **Description**  
---|---  
Graph | The entire agent workflow, represented as a graph (like a tree structure).  
State | A shared object that holds the current snapshot of your application. Immutable – always return a new version of state.  
Node | A Python function that performs a task. It takes in state, does something (like LLM call), and returns a new state.  
Edge | A Python function that determines what node runs next based on the current state. Can be simple or conditional.  
🟠 Nodes do the work, 🔵 Edges decide what happens next.  

🛠️ The 5 Steps to Building a Landgraf Agent  
1. Define the State Class  
    * Holds shared info used by all nodes.  
    * Immutable: always return a new version after updates.  
2. Start a Graph Builder  
    * This is where you define how your workflow is laid out.  
    * Think of it as setting the blueprint before running.  
3. Create Nodes  
    * Each one is a Python function (e.g., LLM call, file write).  
    * Operates on state and returns an updated version.  
4. Create Edges  
    * Define transitions between nodes.  
    * Can be fixed (always runs next) or conditional (based on state).  
5. Compile the Graph  
    * Turns your design into an executable workflow.  
    * After compiling, you can run the graph.  

⚙️ Execution Flow of a Landgraf App  
There are 2 phases when running a graph:  
* Phase 1: Define your agent workflow (the 5 steps above).  
* Phase 2: Run the compiled graph with initial input.  
This two-phase design is different from typical Python scripts and may feel unfamiliar at first — but it gives powerful structure and clarity.  

🧊 What Is Immutable State?  
* Immutable means: once created, the state cannot be modified.  
* Instead of changing it, you:  
    * Read from the current state (e.g., state.count)  
    * Create and return a new state with updated values.  

```python
def my_counting_node(state: MyState):
    new_count = state.count + 1
    return MyState(count=new_count)
```
✅ Helps with traceability and consistency across agent execution.
# 🔁 Reducer Functions: What and Why

## 🧩 Concept Table

| Concept | Description |
|--------|-------------|
| Reducer | A special function tied to a state field that tells Landgraf how to combine values. |
| Purpose | Enables parallel execution of nodes safely. Avoids overwriting updates from other nodes. |

## 🧠 Why It Matters

- If multiple nodes update the same field at the same time, reducer logic safely merges them.
- Without reducers, simultaneous updates would conflict or overwrite each other.

## ✅ Example Scenario

If multiple nodes increment `count`, a reducer might define how to sum values instead of overwrite:

```python
@state.reducer("count")
def combine_counts(old_value, new_value):
    return old_value + new_value
```
## 🛍️ Summary Takeaway

| Principle       | Why It’s Important                                                          |
| --------------- | --------------------------------------------------------------------------- |
| Immutability    | Keeps state clean, traceable, and rollback-friendly.                        |
| Reducers        | Enable safe, parallel execution with no lost updates.                       |
| Two-phase model | First build the graph, then run it — this supports scalability and clarity. |

---

## 🧠 Key Concepts from Landgraf Lab 1 (Week 4)

### 📌 1. We’re Back to Notebooks

* This lab is built in a notebook format (like previous non-Crew weeks).
* Code still plays a central role — don’t worry if you prefer that.

### 🤩 2. What is `Annotated` in Python?

* `Annotated` is used to add metadata to a variable or parameter.
* Python ignores this metadata at runtime — but tools like Landgraf can read it.

```python
from typing import Annotated

def shout(text: Annotated[str, "Something to be shouted"]) -> str:
    return text.upper()
```

> 🟨 This has no runtime effect but gives extra context — useful for tools like Landgraf.

### 🔁 3. Reducers via Annotation

* Landgraf requires you to annotate state fields when using reducers.
* This tells Landgraf how to combine field values when multiple nodes return updates simultaneously.

#### Example setup:

```python
from landgraf.message import add_messages
from pydantic import BaseModel
from typing import Annotated, List

class MyState(BaseModel):
    messages: Annotated[List[str], add_messages]
```

> ✅ `add_messages` is a built-in reducer that simply concatenates lists of messages.

### 🧱 4. Defining Your Graph’s State

* The state is often implemented using a `pydantic.BaseModel` (or `TypedDict`).
* State is immutable — you return a new state object every time.
* ❗ Reducers help merge states when nodes update in parallel — avoiding overwrites.

### 🛠️ 5. Start the Graph Builder

Step 2 of the Landgraf setup process:

```python
from landgraf import StateGraph

graph = StateGraph(MyState)
```

> 🔹 You pass the **class** (not an instance) to `StateGraph`.

---

## ✅ Summary of Steps (So Far)

| Step | Description                                         |
| ---- | --------------------------------------------------- |
| 1    | Define State class with annotated fields & reducers |
| 2    | Start the graph builder using `StateGraph(State)`   |
| 3–5  | Next: Create nodes, edges, and compile the graph    |

---

## 🧠 Key Concepts: Supersteps & Checkpointing in Landgraf

### 🔁 1. What is a Superstep?

* A superstep = one full invocation of a graph.
* Every time the graph is run (e.g. in response to a user input), it's a new superstep.
* Nodes that execute in parallel belong to the same superstep.
* Sequential interactions (like another user input) trigger a new superstep.

✅ Think of each user interaction (message, prompt, etc.) as one superstep.

### 🧹 2. Graph Lifecycle Overview

Each graph run involves:

1. Defining the graph:

   * State class
   * Graph builder
   * Nodes
   * Edges
   * Compilation
2. Invoke the graph with some input → Superstep 1
3. Get output
4. Another input → Superstep 2
5. And so on…

#### 🧠 Visual mental model:

```mathematica
[Graph Definition]
    ↓
[User Input 1] → [Graph Invocation 1] → Output 1
    ↓
[User Input 2] → [Graph Invocation 2] → Output 2
    ↓
...
```

### 🧠 3. Why Are Supersteps Important?

* They're the unit of execution in LangGraph.
* Reducers (used to combine state) only apply within a single superstep.
* To persist and manage state between supersteps, you need checkpointing.

### 📍 4. Checkpointing

* Checkpointing = saving the final state at the end of each superstep.
* On the next invocation (next superstep), LangGraph can resume from this checkpointed state.
* Essential for memory persistence, context tracking, and conversation continuity.

📌 Without checkpointing, your graph starts from scratch every time.

### 🧪 5. What’s Next in Lab

You'll explore:

* How LangSmith logs info
* Tool calling (built-in & custom)
* Implementing checkpointing for memory across interactions

---

## 🧠 LangGraph Checkpointing – Key Points

### 📌 Why Memory Doesn’t Persist by Default

* Even though LangGraph uses state and reducers, that state only exists during a single superstep (one invocation of the graph).
* Without checkpointing, state is lost between supersteps — e.g., the graph won’t remember your name across turns.

### 📀 Checkpointing: How LangGraph Remembers Between Steps

1. **Use `MemorySaver`**

   * Acts as an in-memory checkpoint storage (not a long-term database).
   * Captures the entire state after each superstep.

2. **Pass `checkpointer=memory` when compiling the graph:**

```python
graph = graph.compile(checkpointer=memory)
```

3. **Use a config dict with a thread ID to associate calls with a memory thread:**

```python
config = {
    "configurable": {
        "thread_id": "1"  # identifies the conversation
    }
}
```

4. **Pass config to `graph.invoke()` to tie the call to that memory thread.**

---

## 🧠 How It Works

* State is remembered per thread ID.
* When you change the thread ID, the memory resets (like starting a new conversation).
* When you reuse the same thread ID, LangGraph pulls from the last checkpoint.

## 🔄 Time Travel with LangGraph

You can:

* Call `.get_state(config)` → gives the latest state for a thread.
* Call `.get_state_history(config)` → gives the full history of each superstep's state.
* Use a checkpoint ID to rewind and rerun from a specific past moment.

🕰️ This lets you “time travel” — e.g., replay past conversation states or resume from failure.

---

## 💡 Why This Matters

* Unlike hacks like storing state in UI globals (e.g., in Gradio), checkpointing is:

  * Structured
  * Repeatable
  * Resilient (easy to debug and retry)
# 🌟 Week 5: Autogen Overview

## 🧠 Autogen Overview – Key Concepts & Context

### 🚀 What is Autogen?

* Autogen is an open-source agent framework by **Microsoft**.
* Focused on async, event-driven architecture to enable:

  * Better **observability**
  * Improved **flexibility**, **control**, and **scalability**
* The version used in the course: **v0.5.1** (based on the rewrite that started at v0.4)

---

### 🔀 Big Drama: Two Competing Versions

#### ✅ Microsoft Autogen (v0.4+)

* The **official** track used in this course
* More **structured**, **stable**, and **enterprise-focused**
* Actively supported by Microsoft

#### ⚔️ AG2 (Autogen Gen 2 / AgentOS2)

* **Forked** by original Autogen creators after leaving Microsoft
* Based on **older** version (v0.2) but claims to move faster
* Owns the `autogen` name on **PyPI**:

  * `pip install autogen` installs **AG2**, not Microsoft’s version
* Has taken over original **Discord** and some community spaces

> 📌 **Key Caution**: Always verify if docs/tutorials refer to **AG2** or **Microsoft Autogen**
> — they’re **not compatible**.

---

## 🔧 Autogen Core – Distributed Runtime (Experimental)

### 🧱 What is Autogen Core?

* The **lowest layer** of Autogen.
* A framework for **agent interaction**, not agent implementation.
* Similar to **LangGraph** in structure, but with different focus:

  * **LangGraph** → Focused on **repeatable workflows**
  * **Autogen Core** → Focused on **dynamic agent interactions**

---

### 🚀 Distributed Runtime – Overview

* Enables agents to run across **multiple processes or machines**.

> ⚠️ Still **experimental**:
>
> * APIs may change
> * Not production-ready — more of a **preview**

---

## 🧩 Two Main Components

### 1. Host Service

* Acts as a **container and coordinator**.
* Responsibilities:

  * Handles **message delivery**
  * Manages **agent sessions**
  * Uses **gRPC** for cross-machine/process communication

### 2. Worker Runtime

* Manages **actual agent instances**
* Responsibilities:

  * Hosts and executes **agent logic**
  * Registers available agents with the **host**
  * Handles **execution** during tasks

---

## 🌐 What It Enables

* **Multi-agent systems** distributed across machines or languages
* **Separation** of infrastructure and logic:

  * **Host** deals with communication
  * **Worker** handles agent behavior

# ⭐️ Week 6: The Pinnacle

## 🧱 What's Happening This Week?

1. Introduction to MCP (Model Context Protocol) by Anthropic
2. Return to the OpenAI Agents SDK (used alongside MCP)

---

## 🛠️ Quick Recap of Framework Journey So Far:

* **Week 1**: Raw tools and APIs
* **Week 2**: OpenAI Agents SDK
* **Week 3**: Crew (structured, YAML-first)
* **Week 4**: LangGraph (graph-style agent coordination)
* **Week 5**: Autogen (multi-agent, experimental, with Autogen Core)
* **Week 6**: **MCP** – not a framework, but a **standard**

---

## ❓ What MCP Is Not

* Not an agent framework (unlike Crew or OpenAI SDK)
* Not used to build agents directly
* Not a fundamental rework of how agents function
* Does not include tools — it defines how to integrate them

---

## ✅ What MCP Is

* A **protocol / standard**: Defines how agents access tools, resources, and prompts
* Think of it as the **USB-C of AI**: a universal connector for agent functionality

### Enables:

* Tool integration (most hyped use case)
* Resources (e.g., context providers)
* Prompt templates

---

## 🤔 Why Might You Be Skeptical?

* Feels like just another spec
* Frameworks like LangChain already support tool ecosystems
* You can always write your own tools manually

---

## 💡 Why It’s Exciting

* **Frictionless integration**: Easier than custom JSON or framework-specific tool wrappers
* **Framework-agnostic**: Works with Autogen, LangChain, OpenAI Agents SDK, etc.
* **Exploding adoption**: Big network effects + active community
* **Tons of MCP tools already available**: Ready-to-use marketplace ecosystem
* **Backed by Anthropic**: A major AI player giving it legitimacy and traction
* **Standards matter**: Like HTML, a well-adopted protocol becomes foundational

---

## ⟳ Final Thought

> MCP doesn’t replace frameworks — it **complements** them by making tool access universal and standardized.

---

## 🧠 MCP Core Concepts (Three Key Components)

### 1. Host

* The application or environment using the tools.
* Examples:

  * Claude Desktop App (most common)
  * Cursor
  * Your custom agent app
* Important: Claude **web chat is not a host**, only the desktop app is (as of now).

### 2. MCP Client

* Lives inside the host
* Connects the host to one or more MCP Servers
* One MCP client per MCP server
* Examples:

  * One client for Google Maps tools
  * One for file system access
  * One for stock market lookups

### 3. MCP Server

* A process that provides tools, resources (context), or prompt templates.
* Think of it like a plugin provider.
* Examples:

  * A server that provides weather lookup via a weather API
  * A file system access server
  * A web page fetcher (e.g., “Fetcher” using Playwright)

---

## 📦 How It All Connects (Summary):

**Your app (Host)** → has **MCP clients** → which connect to **MCP servers** → that expose **tools** to use.

---

## 🧱 3 Architecture Models (Where Servers Run):

1. **Local-Local**: Client + server run locally; work done locally.
2. **Local + External API**: Server runs locally, but connects to external APIs (like Google or Slack).
3. **Local-Remote**: MCP server is on a remote machine. Less common, but supported.

> ⟳ Most common: #2 — server on your machine, calling out to APIs.

---

### ⟳ Common Misconception:

* People often think MCP servers must be remote.
* Truth: Most MCP servers are **run locally**, even if they access remote APIs.

---

## 📡 Communication Mechanisms (Transports)

| Transport | Use Case | Tech                  | Notes                          |
| --------- | -------- | --------------------- | ------------------------------ |
| `stdio`   | Local    | Standard Input/Output | Most common for local servers  |
| `sse`     | Remote   | HTTPS + SSE           | Used for streaming remote data |

---

## 🔌 Analogy

> Think of MCP as a **universal socket system** — like USB-C — for plugging tools into agent apps.

---

## 🎯 What Makes This Powerful

* Simple lines of code = powerful actions:

  * Web scraping
  * File generation
* Thousands of ready-to-use tools available in MCP marketplaces like:

  * MCP
  * Smithery
  * GlamourAI

---

## 🏭 Marketplaces: A Tool Zoo

* Thousands of tools (e.g., Slack, GitHub, Google Drive, Weather, Time, Blender)
* Some run locally but call remote APIs
* Others can be remote MCP servers
* Sites like Hugging Face Community Blog share highlights and best MCP tools

---

## 💡 Final Insights

* Yes, MCP is that simple — just a **standard for tool access**
* Its **simplicity is the power**: plug-and-play tool expansion
* **Next step**: build your own MCP server and client
