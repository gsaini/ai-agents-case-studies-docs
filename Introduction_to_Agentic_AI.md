# Introduction to Agentic AI

> A comprehensive guide to understanding Agentic AI, its key characteristics, how it differs from traditional AI paradigms, the role of rational agents in autonomous decision-making, and how agents communicate using the Model Context Protocol (MCP).

---

## Table of Contents

1. [Overview & Learning Objectives](#overview--learning-objectives)
2. [What Is Agentic AI?](#what-is-agentic-ai)
3. [Agentic AI vs. Traditional AI](#agentic-ai-vs-traditional-ai)
4. [Rational Agents & Autonomous Decision-Making](#rational-agents--autonomous-decision-making)
5. [Agentic Workflows](#agentic-workflows)
6. [Model Context Protocol (MCP)](#model-context-protocol-mcp)
7. [Building Your First Agent](#building-your-first-agent)
8. [Study Questions & Discussion Prompts](#study-questions--discussion-prompts)
9. [Resources & References](#resources--references)

---

## Overview & Learning Objectives

This week introduces the paradigm of **Agentic AI** — a transformational shift from traditional AI systems that simply respond to prompts to systems that **plan, act, observe, and adapt** autonomously. You'll learn what makes an AI system "agentic," explore the foundations of rational agents, understand how agentic workflows orchestrate complex tasks, and discover the **Model Context Protocol (MCP)** — the emerging standard for agent-to-tool communication.

### After completing this module, you should be able to:

- [ ] Define Agentic AI and its key characteristics
- [ ] Distinguish agentic systems from traditional AI paradigms (chatbots, classifiers, generators)
- [ ] Explain the concept of rational agents and their role in autonomous decision-making
- [ ] Describe and compare different agentic workflow patterns
- [ ] Understand the architecture and purpose of the Model Context Protocol (MCP)
- [ ] Identify practical use cases for agentic AI in enterprise and consumer applications
- [ ] Evaluate when to use agentic vs. non-agentic approaches

---

## What Is Agentic AI?

### Definition

**Agentic AI** refers to artificial intelligence systems that can **autonomously plan, reason, and execute multi-step tasks** to achieve goals, with the ability to use tools, interact with environments, and adapt their strategies based on feedback — all with minimal human intervention.

```
┌─────────────────────────────────────────────────────────────────┐
│                     WHAT MAKES AI "AGENTIC"?                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│        Traditional AI               Agentic AI                   │
│        ──────────────               ──────────                   │
│        Input → Output               Goal → Plan → Act → Observe │
│        Single-turn                   Multi-turn & multi-step     │
│        Reactive                      Proactive                   │
│        Stateless                     Stateful (memory)           │
│        No tool use                   Tool-equipped               │
│        Human-directed                Self-directed               │
│                                                                  │
│   An AI system is "agentic" when it:                             │
│                                                                  │
│   ✅ Pursues goals over multiple steps                           │
│   ✅ Plans and reasons about how to achieve them                 │
│   ✅ Takes actions in the real world (tools, APIs, code exec)    │
│   ✅ Observes the results of its actions                         │
│   ✅ Adapts its strategy based on feedback                       │
│   ✅ Operates with some degree of autonomy                      │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### The Five Pillars of Agentic AI

```
┌─────────────────────────────────────────────────────────────────┐
│                   FIVE PILLARS OF AGENTIC AI                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐          │
│  │   AUTONOMY   │  │ GOAL-DRIVEN  │  │ ADAPTABILITY │          │
│  │              │  │   BEHAVIOR   │  │              │          │
│  │ Acts without │  │              │  │ Learns and   │          │
│  │ constant     │  │ Pursues      │  │ adjusts      │          │
│  │ human        │  │ specific     │  │ strategies   │          │
│  │ direction    │  │ objectives   │  │ from         │          │
│  │              │  │ proactively  │  │ feedback     │          │
│  └──────────────┘  └──────────────┘  └──────────────┘          │
│                                                                  │
│  ┌──────────────┐  ┌──────────────┐                             │
│  │  TOOL USE    │  │  REASONING   │                             │
│  │              │  │              │                             │
│  │ Interacts    │  │ Plans and    │                             │
│  │ with         │  │ decomposes   │                             │
│  │ external     │  │ complex      │                             │
│  │ systems and  │  │ problems     │                             │
│  │ APIs         │  │ into steps   │                             │
│  └──────────────┘  └──────────────┘                             │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

| Pillar                   | Description                                                                                                          | Example                                                                                                                        |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **Autonomy**             | Operates independently within defined parameters, making decisions without requiring human approval for every action | A coding agent that independently identifies bugs, writes fixes, runs tests, and iterates                                      |
| **Goal-Driven Behavior** | Focuses on achieving specific objectives; can break complex goals into manageable sub-tasks                          | A research agent tasked with "find the best cloud provider for our workload"                                                   |
| **Adaptability**         | Continuously learns from interactions and feedback; adjusts approach when initial strategies fail                    | An agent that switches from web search to database query when search results are insufficient                                  |
| **Tool Use**             | Accesses external tools, APIs, databases, file systems, and code execution environments                              | An agent calling a calculator, searching the web, executing Python code, or querying a database                                |
| **Reasoning**            | Employs multi-step reasoning (Chain-of-Thought, ReAct) to plan actions and evaluate outcomes                         | An agent that thinks: "I need to find the user's order → query the database → check the shipping status → format the response" |

### The Spectrum of Agency

Not all AI systems are equally "agentic." Agency exists on a spectrum:

```
┌─────────────────────────────────────────────────────────────────┐
│                    SPECTRUM OF AGENCY                             │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  LEVEL 0         LEVEL 1          LEVEL 2          LEVEL 3       │
│  No Agency       Assisted         Semi-Autonomous  Autonomous    │
│                                                                  │
│  ╠════════════╬════════════════╬════════════════╬══════════════╣ │
│  │            │                │                │              │ │
│  Chatbot      Copilot          Agent w/         Fully          │ │
│  (responds    (suggests,       Human-in-Loop    Autonomous     │ │
│  to prompts)  human decides)   (acts, human     Agent          │ │
│                                 approves)       (self-directed)│ │
│                                                                  │
│  Examples:     Examples:        Examples:        Examples:       │
│  ChatGPT       GitHub Copilot   Devin (coding)   Future goal    │
│  Q&A bots      Writing assist   Claude Code      Self-driving   │
│  Classifiers   Auto-suggest     Trading bots     infrastructure │
│                                                                  │
│  ← Less Autonomy                    More Autonomy →              │
│  ← More Human Control               Less Human Control →        │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## Agentic AI vs. Traditional AI

### Paradigm Comparison

```
┌─────────────────────────────────────────────────────────────────┐
│              EVOLUTION OF AI PARADIGMS                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ERA 1: RULE-BASED AI (1950s-1990s)                              │
│  ─────────────────────────────────                               │
│  IF condition THEN action                                        │
│  Expert systems, decision trees                                  │
│  Brittle, manually programmed                                    │
│                                                                  │
│  ERA 2: MACHINE LEARNING (2000s-2010s)                           │
│  ──────────────────────────────────────                          │
│  Learn patterns from data                                        │
│  Classification, regression, clustering                          │
│  Narrow tasks, needs labeled data                                │
│                                                                  │
│  ERA 3: DEEP LEARNING & GENERATIVE AI (2017-2023)                │
│  ─────────────────────────────────────────────────               │
│  Transformers, GPT, DALL-E, Stable Diffusion                     │
│  Content generation, language understanding                      │
│  Powerful but reactive, single-turn                              │
│                                                                  │
│  ERA 4: AGENTIC AI (2024-Present) ← WE ARE HERE                 │
│  ────────────────────────────────                                │
│  Autonomous goal pursuit with tools                              │
│  Multi-step planning and execution                               │
│  Self-correcting, environment-aware                              │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Detailed Feature Comparison

| Feature                     | Traditional AI / LLM                             | Agentic AI                                         |
| --------------------------- | ------------------------------------------------ | -------------------------------------------------- |
| **Interaction Model**       | Single prompt → single response                  | Goal → multi-step plan → iterative execution       |
| **Reasoning**               | One-shot (may use CoT)                           | Multi-step, iterative reasoning with ReAct loops   |
| **Memory**                  | Context window only (stateless between sessions) | Short-term + long-term memory, state persistence   |
| **Tool Use**                | None or limited function calling                 | Rich tool ecosystem (APIs, code, databases, files) |
| **Error Handling**          | Returns best guess; user must retry              | Self-detects errors, retries, and adapts strategy  |
| **Planning**                | Implicit in single generation                    | Explicit task decomposition and planning           |
| **Environment Interaction** | No side effects                                  | Reads/writes files, executes code, sends messages  |
| **Autonomy**                | Fully human-directed                             | Varies from assisted to fully autonomous           |
| **Scope**                   | Bounded to single request                        | Can span multiple sessions and contexts            |
| **Feedback Loop**           | None (open-loop)                                 | Observes results, adjusts approach (closed-loop)   |

### The ReAct Pattern — The Engine of Agentic AI

Most modern agentic AI systems are built on the **ReAct (Reasoning + Acting)** pattern:

```
┌─────────────────────────────────────────────────────────────────┐
│                     THE ReAct LOOP                                │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│                      ┌──────────┐                                │
│            ┌────────→│  THINK   │                                │
│            │         │ (Reason) │                                │
│            │         └────┬─────┘                                │
│            │              │                                      │
│            │              ▼                                      │
│            │         ┌──────────┐                                │
│            │         │   ACT    │                                │
│            │         │ (Tool)   │                                │
│            │         └────┬─────┘                                │
│            │              │                                      │
│            │              ▼                                      │
│            │         ┌──────────┐                                │
│            │         │ OBSERVE  │                                │
│            │         │ (Result) │                                │
│            │         └────┬─────┘                                │
│            │              │                                      │
│            │   ┌──────────┴──────────┐                           │
│            │   │ Goal achieved?      │                           │
│            │   ├─── NO ──→ Continue ─┘                           │
│            │   │                                                 │
│            │   └─── YES ──→ Return Final Answer                  │
│            │                                                     │
│            └─────────── (loop) ──────────────┘                   │
│                                                                  │
│  Example Trace:                                                  │
│  ─────────────                                                   │
│  THOUGHT: I need to find the user's order status.                │
│           Let me search the database.                            │
│  ACTION:  query_database("SELECT status FROM orders              │
│           WHERE order_id = 'ORD-12345'")                         │
│  OBSERVE: Result: {"status": "shipped", "tracking": "1Z999..."}  │
│  THOUGHT: I found the order. It's been shipped. Let me           │
│           get the delivery estimate.                             │
│  ACTION:  check_tracking("1Z999...")                             │
│  OBSERVE: Result: {"est_delivery": "Feb 15, 2026"}              │
│  THOUGHT: I have all the information. Let me respond.            │
│  ANSWER:  "Your order ORD-12345 has been shipped! Tracking:      │
│           1Z999..., estimated delivery: Feb 15, 2026."           │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

**Key Paper:** Yao et al., "ReAct: Synergizing Reasoning and Acting in Language Models" — https://arxiv.org/abs/2210.03629

---

## Rational Agents & Autonomous Decision-Making

### What Is a Rational Agent?

A **rational agent** is an entity that perceives its environment through **sensors**, reasons about the best course of action, and acts upon the environment through **actuators** to **maximize a performance measure**.

```
┌─────────────────────────────────────────────────────────────────┐
│                    RATIONAL AGENT ARCHITECTURE                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│                        ENVIRONMENT                               │
│     ┌─────────────────────────────────────────────────┐         │
│     │                                                 │         │
│     │   ┌──────────┐        ┌──────────┐              │         │
│     │   │ Percepts │        │ Actions  │              │         │
│     │   │ (input)  │        │ (output) │              │         │
│     │   └────┬─────┘        └────▲─────┘              │         │
│     │        │                   │                    │         │
│     └────────┼───────────────────┼────────────────────┘         │
│              │                   │                              │
│     ┌────────▼───────────────────┴────────────────────┐         │
│     │                   AGENT                          │         │
│     │                                                  │         │
│     │   ┌──────────┐  ┌──────────┐  ┌──────────┐     │         │
│     │   │ SENSORS  │→ │  BRAIN   │→ │ACTUATORS │     │         │
│     │   │          │  │  (LLM +  │  │(Tools &  │     │         │
│     │   │ (Input   │  │ Reasoning│  │ APIs)    │     │         │
│     │   │  Parser) │  │  Engine) │  │          │     │         │
│     │   └──────────┘  └────┬─────┘  └──────────┘     │         │
│     │                      │                          │         │
│     │               ┌──────┴──────┐                   │         │
│     │               │   MEMORY    │                   │         │
│     │               │ (State &    │                   │         │
│     │               │  Context)   │                   │         │
│     │               └─────────────┘                   │         │
│     │                                                  │         │
│     └──────────────────────────────────────────────────┘         │
│                                                                  │
│   Rational Action = argmax_a Σ P(result | action) × U(result)   │
│                                                                  │
│   "For each possible action, consider the probability of each   │
│    outcome and its utility. Choose the action that maximizes     │
│    expected utility."                                            │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Types of Agents (Russell & Norvig Classification)

```
┌─────────────────────────────────────────────────────────────────┐
│                    AGENT TYPE HIERARCHY                           │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌───────────────────────────────────────────────────────┐      │
│  │ 1. SIMPLE REFLEX AGENT                                 │      │
│  │    Percept → IF-THEN Rules → Action                    │      │
│  │    No memory, no planning                              │      │
│  │    Example: Thermostat, spam filter                     │      │
│  └───────────────────┬───────────────────────────────────┘      │
│                      ▼                                          │
│  ┌───────────────────────────────────────────────────────┐      │
│  │ 2. MODEL-BASED REFLEX AGENT                            │      │
│  │    Percept + Internal Model → Rules → Action           │      │
│  │    Maintains internal state of the world               │      │
│  │    Example: Anti-lock braking system                    │      │
│  └───────────────────┬───────────────────────────────────┘      │
│                      ▼                                          │
│  ┌───────────────────────────────────────────────────────┐      │
│  │ 3. GOAL-BASED AGENT                                    │      │
│  │    Percept + Model + Goals → Planning → Action         │      │
│  │    Can plan and simulate future states                  │      │
│  │    Example: GPS navigation agent                        │      │
│  └───────────────────┬───────────────────────────────────┘      │
│                      ▼                                          │
│  ┌───────────────────────────────────────────────────────┐      │
│  │ 4. UTILITY-BASED AGENT                                 │      │
│  │    Percept + Model + Utility Function → Action         │      │
│  │    Optimizes for "happiness" / expected utility         │      │
│  │    Can make trade-offs between conflicting goals        │      │
│  │    Example: Stock trading agent                         │      │
│  └───────────────────┬───────────────────────────────────┘      │
│                      ▼                                          │
│  ┌───────────────────────────────────────────────────────┐      │
│  │ 5. LEARNING AGENT                                      │      │
│  │    All of the above + Learning Component               │      │
│  │    Improves performance over time                       │      │
│  │    Has: Performance Element, Critic, Learning Element,  │      │
│  │         Problem Generator                               │      │
│  │    Example: Modern LLM-based agents with RLHF           │      │
│  └───────────────────────────────────────────────────────┘      │
│                                                                  │
│  INCREASING CAPABILITY ↓                                        │
│  Simple Reflex → Model-Based → Goal-Based → Utility → Learning  │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Agent Type Comparison

| Agent Type             | Memory              | Planning         | Learning | Flexibility | LLM Equivalent           |
| ---------------------- | ------------------- | ---------------- | -------- | ----------- | ------------------------ |
| **Simple Reflex**      | None                | None             | None     | Very Low    | Zero-shot prompt         |
| **Model-Based Reflex** | Internal state      | None             | None     | Low         | Few-shot with context    |
| **Goal-Based**         | State + goals       | Yes              | None     | Medium      | ReAct agent              |
| **Utility-Based**      | State + preferences | Yes (optimizing) | None     | High        | Agent with reward model  |
| **Learning**           | State + experience  | Yes              | Yes      | Very High   | Agent with RLHF + memory |

### Decision-Making Process in Agentic AI

```
┌─────────────────────────────────────────────────────────────────┐
│              AUTONOMOUS DECISION-MAKING PIPELINE                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  1. PERCEIVE                                                     │
│     ┌─────────────────────────────────────────────┐             │
│     │ • Receive user goal / instruction            │             │
│     │ • Gather context from environment            │             │
│     │ • Retrieve relevant memories                 │             │
│     │ • Read tool descriptions and capabilities    │             │
│     └─────────────────────────┬───────────────────┘             │
│                               ▼                                  │
│  2. REASON                                                       │
│     ┌─────────────────────────────────────────────┐             │
│     │ • Analyze the current situation              │             │
│     │ • Decompose goal into sub-tasks              │             │
│     │ • Evaluate possible strategies               │             │
│     │ • Select the best course of action           │             │
│     │ • (Uses CoT, ToT, or reasoning traces)       │             │
│     └─────────────────────────┬───────────────────┘             │
│                               ▼                                  │
│  3. ACT                                                          │
│     ┌─────────────────────────────────────────────┐             │
│     │ • Execute selected action (tool call)        │             │
│     │ • Interact with external systems             │             │
│     │ • Modify environment if needed               │             │
│     └─────────────────────────┬───────────────────┘             │
│                               ▼                                  │
│  4. OBSERVE                                                      │
│     ┌─────────────────────────────────────────────┐             │
│     │ • Capture action results                     │             │
│     │ • Check for errors or unexpected outcomes    │             │
│     │ • Update internal state / memory             │             │
│     └─────────────────────────┬───────────────────┘             │
│                               ▼                                  │
│  5. EVALUATE                                                     │
│     ┌─────────────────────────────────────────────┐             │
│     │ • Is the goal achieved?                      │             │
│     │   → YES: Return result to user               │             │
│     │   → NO:  Return to Step 2 (REASON)           │             │
│     │ • Should I adjust strategy?                  │             │
│     │ • Have I hit resource limits?                 │             │
│     └─────────────────────────────────────────────┘             │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## Agentic Workflows

### What Are Agentic Workflows?

**Agentic workflows** are structured patterns for orchestrating AI agents to accomplish complex, multi-step tasks. They define how agents interact with tools, data sources, and each other.

### The Five Canonical Workflow Patterns

_(Based on Anthropic's "Building Effective Agents" guide)_

#### Pattern 1: Prompt Chaining

```
┌─────────────────────────────────────────────────────────────┐
│  PROMPT CHAINING                                             │
│  ────────────────                                            │
│                                                              │
│  Task → [LLM Call 1] → Gate → [LLM Call 2] → Output         │
│              │           │                                   │
│         "Generate        "Is it                              │
│          outline"        good?"                              │
│                     YES → continue                           │
│                     NO  → retry / refine                     │
│                                                              │
│  USE WHEN: Task naturally decomposes into fixed sub-tasks    │
│  EXAMPLE: Generate marketing copy → Translate → Review       │
│                                                              │
│  ✅ Simple, predictable, easy to debug                       │
│  ❌ Fixed pipeline, can't adapt to unexpected situations     │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

#### Pattern 2: Routing

```
┌─────────────────────────────────────────────────────────────┐
│  ROUTING                                                     │
│  ───────                                                     │
│                                                              │
│            ┌───→ Route A: Simple Query Handler               │
│            │                                                 │
│  Input → [Classifier] ─→ Route B: Complex Analysis          │
│            │                                                 │
│            └───→ Route C: Specialized Domain Expert          │
│                                                              │
│  USE WHEN: Different input types need different handling     │
│  EXAMPLE: Customer support — billing vs. technical vs. sales │
│                                                              │
│  ✅ Efficient resource use, specialized handling             │
│  ❌ Requires good classification; edge cases may mis-route   │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

#### Pattern 3: Parallelization

```
┌─────────────────────────────────────────────────────────────┐
│  PARALLELIZATION                                             │
│  ───────────────                                             │
│                                                              │
│  SECTIONING (Independent sub-tasks):                         │
│                                                              │
│            ┌───→ [LLM: Analyze sentiment]  ──┐               │
│  Input ────┼───→ [LLM: Extract entities]   ──┼──→ Aggregate  │
│            └───→ [LLM: Summarize content]  ──┘               │
│                                                              │
│  VOTING (Same task, multiple perspectives):                   │
│                                                              │
│            ┌───→ [LLM Instance 1: Answer]  ──┐               │
│  Input ────┼───→ [LLM Instance 2: Answer]  ──┼──→ Majority   │
│            └───→ [LLM Instance 3: Answer]  ──┘     Vote      │
│                                                              │
│  USE WHEN: Speed matters OR multiple perspectives help       │
│  EXAMPLE: Code review (security + quality + style in parallel)│
│                                                              │
│  ✅ Faster, more robust outputs                              │
│  ❌ Higher compute cost, needs aggregation logic             │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

#### Pattern 4: Orchestrator-Workers

```
┌─────────────────────────────────────────────────────────────┐
│  ORCHESTRATOR-WORKERS                                        │
│  ────────────────────                                        │
│                                                              │
│                          ┌──→ [Worker 1: Research] ───┐      │
│  Input → [Orchestrator] ─┼──→ [Worker 2: Analyze]  ───┼→ Out │
│              │    ▲      └──→ [Worker 3: Draft]    ───┘      │
│              │    │                                           │
│              │    └──── (Dynamic task assignment)             │
│              │                                               │
│  The Orchestrator:                                           │
│  • Decomposes the task dynamically                           │
│  • Assigns sub-tasks to specialized workers                  │
│  • Monitors progress and adjusts                             │
│  • Synthesizes final result                                  │
│                                                              │
│  USE WHEN: Complex tasks with unpredictable sub-tasks        │
│  EXAMPLE: "Research and write a report on market trends"     │
│                                                              │
│  ✅ Flexible, handles complex multi-step tasks               │
│  ❌ More complex to implement, orchestrator is a bottleneck  │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

#### Pattern 5: Evaluator-Optimizer

```
┌─────────────────────────────────────────────────────────────┐
│  EVALUATOR-OPTIMIZER                                         │
│  ────────────────────                                        │
│                                                              │
│  ┌──────────────────────────────────────────────┐            │
│  │                                              │            │
│  │  [Generator] → Output → [Evaluator] → Score  │            │
│  │      ▲                       │               │            │
│  │      │                       │               │            │
│  │      └──── Feedback ─────────┘               │            │
│  │           (If score < threshold,              │            │
│  │            regenerate with feedback)          │            │
│  │                                              │            │
│  └──────────────────────────────────────────────┘            │
│                                                              │
│  USE WHEN: Clear evaluation criteria exist, quality matters  │
│  EXAMPLE: Code generation → test execution → fix errors      │
│                                                              │
│  ✅ Produces high-quality output through iteration           │
│  ❌ Can loop indefinitely; needs termination conditions      │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### Workflow Pattern Selection Guide

| Pattern                  | Complexity | Flexibility | Best For                                             |
| ------------------------ | ---------- | ----------- | ---------------------------------------------------- |
| **Prompt Chaining**      | Low        | Low         | Fixed-step pipelines (translate → review → publish)  |
| **Routing**              | Low        | Medium      | Multi-category inputs (support tickets, query types) |
| **Parallelization**      | Medium     | Medium      | Independent sub-tasks, voting for reliability        |
| **Orchestrator-Workers** | High       | High        | Complex, dynamic tasks with unknown sub-task count   |
| **Evaluator-Optimizer**  | Medium     | Medium      | Quality-critical outputs (code, writing, analysis)   |

### From Workflows to Agents

```
┌─────────────────────────────────────────────────────────────────┐
│              WORKFLOWS vs. AGENTS (Anthropic's Distinction)      │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  WORKFLOWS                          AGENTS                       │
│  ─────────                          ──────                       │
│  LLMs and tools orchestrated        LLMs dynamically direct      │
│  through PREDEFINED code paths      their OWN processes and      │
│                                     tool usage                   │
│                                                                  │
│  • Steps are predetermined          • Steps are decided at       │
│  • Human designs the flow             runtime by the LLM         │
│  • Predictable execution            • Emergent behavior          │
│  • Easier to debug and test         • More flexible but harder   │
│                                       to predict                 │
│                                                                  │
│  GOLDEN RULE:                                                    │
│  "Start with workflows. Add agent autonomy only when needed."   │
│                                                                  │
│  ┌────────────────────────────────────────────────────────┐     │
│  │ Simple LLM Call → Workflow (fixed) → Agent (dynamic)   │     │
│  │ ──────────────────────────────────────────────────────  │     │
│  │ ← Less Complex, More Predictable                       │     │
│  │                         More Flexible, Less Predictable→│     │
│  └────────────────────────────────────────────────────────┘     │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## Model Context Protocol (MCP)

### What Is MCP?

The **Model Context Protocol (MCP)** is an open protocol designed by Anthropic (launched November 2024) that standardizes how AI systems integrate with external tools, data sources, and services. Think of it as **"USB-C for AI"** — a universal connector that eliminates the need for custom integrations.

```
┌─────────────────────────────────────────────────────────────────┐
│              THE PROBLEM MCP SOLVES                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  BEFORE MCP (The N×M Problem):                                   │
│  ──────────────────────────────                                  │
│                                                                  │
│  App 1 ──custom──→ Tool A         N apps × M tools =             │
│  App 1 ──custom──→ Tool B         N×M custom integrations        │
│  App 2 ──custom──→ Tool A                                        │
│  App 2 ──custom──→ Tool C         Every app needs custom code    │
│  App 3 ──custom──→ Tool B         for every tool. Doesn't scale!│
│  App 3 ──custom──→ Tool C                                        │
│                                                                  │
│  AFTER MCP (The N+M Solution):                                   │
│  ──────────────────────────────                                  │
│                                                                  │
│  App 1 ──┐                  ┌──→ Tool A                          │
│  App 2 ──┤── MCP Protocol ──┤──→ Tool B                          │
│  App 3 ──┘                  └──→ Tool C                          │
│                                                                  │
│  N apps + M tools = N+M integrations                             │
│  Build once, connect everywhere!                                 │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### MCP Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│              MCP ARCHITECTURE                                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌────────────────────────────────────────────────┐              │
│  │                MCP HOST                         │              │
│  │    (AI Application: Claude, IDE, Custom App)    │              │
│  │                                                 │              │
│  │    ┌──────────────┐    ┌──────────────┐        │              │
│  │    │  MCP Client  │    │  MCP Client  │   ...  │              │
│  │    │  (1:1 with   │    │  (1:1 with   │        │              │
│  │    │   server)    │    │   server)    │        │              │
│  │    └──────┬───────┘    └──────┬───────┘        │              │
│  │           │                   │                │              │
│  └───────────┼───────────────────┼────────────────┘              │
│              │                   │                               │
│         JSON-RPC 2.0        JSON-RPC 2.0                        │
│         (stdio/SSE)         (stdio/SSE)                         │
│              │                   │                               │
│  ┌───────────┼───────────┐  ┌───┼───────────────────┐           │
│  │    MCP Server A        │  │    MCP Server B        │           │
│  │                        │  │                        │           │
│  │  ┌──────────────────┐  │  │  ┌──────────────────┐  │           │
│  │  │    RESOURCES      │  │  │  │    RESOURCES      │  │           │
│  │  │  (Read-only data) │  │  │  │  (Database rows) │  │           │
│  │  ├──────────────────┤  │  │  ├──────────────────┤  │           │
│  │  │    TOOLS          │  │  │  │    TOOLS          │  │           │
│  │  │  (Executable      │  │  │  │  (SQL queries,   │  │           │
│  │  │   functions)      │  │  │  │   CRUD ops)      │  │           │
│  │  ├──────────────────┤  │  │  ├──────────────────┤  │           │
│  │  │    PROMPTS        │  │  │  │    PROMPTS        │  │           │
│  │  │  (Templated       │  │  │  │  (Domain-specific │ │           │
│  │  │   interactions)   │  │  │  │   templates)      │  │           │
│  │  └──────────────────┘  │  │  └──────────────────┘  │           │
│  │                        │  │                        │           │
│  │  ┌──────────────────┐  │  │  ┌──────────────────┐  │           │
│  │  │  Local Data       │  │  │  │  Remote API       │  │           │
│  │  │  (Files, DB)      │  │  │  │  (REST, GraphQL)  │  │           │
│  │  └──────────────────┘  │  │  └──────────────────┘  │           │
│  └────────────────────────┘  └────────────────────────┘           │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### MCP Core Concepts

#### The Three Primitives

| Primitive     | Description                                           | Direction       | Example                                            |
| ------------- | ----------------------------------------------------- | --------------- | -------------------------------------------------- |
| **Resources** | Read-only data that provides context to the AI        | Server → Client | File contents, database records, API responses     |
| **Tools**     | Executable functions the AI can invoke to take action | Client → Server | Run SQL query, send email, create file, search web |
| **Prompts**   | Templated interaction patterns for common tasks       | Server → Client | "Summarize this document", "Generate SQL for..."   |

#### Communication Protocol

```
┌─────────────────────────────────────────────────────────────┐
│              MCP COMMUNICATION FLOW                          │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  1. INITIALIZATION                                           │
│     Client                    Server                         │
│       │── initialize ──────────→│                            │
│       │←── initialize result ──│  (Exchange capabilities)    │
│       │── initialized ─────────→│                            │
│                                                              │
│  2. DISCOVERY                                                │
│       │── tools/list ──────────→│                            │
│       │←── tools listing ──────│  (What can you do?)         │
│       │── resources/list ──────→│                            │
│       │←── resources listing ──│  (What data do you have?)   │
│                                                              │
│  3. INVOCATION                                               │
│       │── tools/call ──────────→│                            │
│       │   {name: "search",     │                             │
│       │    args: {query: "..."}}│                             │
│       │←── tool result ────────│  (Here's what I found)      │
│                                                              │
│  4. RESOURCE ACCESS                                          │
│       │── resources/read ──────→│                            │
│       │   {uri: "file:///..."}  │                             │
│       │←── resource content ───│  (Here's the data)          │
│                                                              │
│  TRANSPORT: JSON-RPC 2.0 over stdio or HTTP SSE              │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### MCP in the Ecosystem

#### Adoption Timeline

| Date         | Milestone                                                          |
| ------------ | ------------------------------------------------------------------ |
| **Nov 2024** | Anthropic launches MCP as open-source                              |
| **Mar 2025** | OpenAI officially adopts MCP                                       |
| **Mid 2025** | Google DeepMind, Microsoft integrate MCP support                   |
| **Dec 2025** | MCP donated to Agentic AI Foundation (AAIF) under Linux Foundation |
| **2026+**    | Industry-wide standard for agent-tool communication                |

#### Who Uses MCP?

| Category             | Adopters                                             |
| -------------------- | ---------------------------------------------------- |
| **AI Providers**     | Anthropic (Claude), OpenAI, Google DeepMind          |
| **IDEs & Dev Tools** | JetBrains, Zed, Replit, Codeium, Sourcegraph, Cursor |
| **Frameworks**       | LangChain, LlamaIndex, Hugging Face                  |
| **SDKs Available**   | Python, TypeScript, C# (Microsoft), Java             |

### MCP vs. Traditional Function Calling

| Feature              | Function Calling (OpenAI-style) | Model Context Protocol          |
| -------------------- | ------------------------------- | ------------------------------- |
| **Scope**            | Single model provider           | Universal, cross-provider       |
| **Discovery**        | Functions predefined in prompt  | Dynamic server discovery        |
| **Data Access**      | Function args/returns only      | Resources + Tools + Prompts     |
| **Transport**        | HTTP API call                   | JSON-RPC 2.0 (stdio/SSE)        |
| **Standardization**  | Provider-specific               | Open standard                   |
| **Multi-connection** | Single provider                 | Multiple servers simultaneously |
| **State**            | Stateless per call              | Persistent session              |

### Building an MCP Server (Conceptual Example)

```python
# Example: A simple MCP server using the Python SDK
from mcp.server import Server
from mcp.types import Resource, Tool, TextContent

# Create server instance
server = Server("my-data-server")

# Define a RESOURCE (read-only data)
@server.resource("db://users/{user_id}")
async def get_user(user_id: str) -> Resource:
    """Get user profile data"""
    user = await database.get_user(user_id)
    return Resource(
        uri=f"db://users/{user_id}",
        name=f"User: {user.name}",
        contents=[TextContent(text=user.to_json())]
    )

# Define a TOOL (executable action)
@server.tool("search_orders")
async def search_orders(query: str, limit: int = 10) -> list[TextContent]:
    """Search customer orders by query string"""
    results = await database.search(query, limit=limit)
    return [TextContent(text=result.to_json()) for result in results]

# Define a PROMPT (templated interaction)
@server.prompt("analyze_customer")
async def analyze_prompt(customer_id: str) -> str:
    """Generate a prompt for customer analysis"""
    return f"""Analyze the following customer's purchase history,
    identify trends, and suggest next-best-actions.
    Customer ID: {customer_id}"""

# Run the server
if __name__ == "__main__":
    server.run(transport="stdio")
```

### MCP Reference Servers

Anthropic provides open-source reference implementations:

| Server                                      | Description                | Data Source      |
| ------------------------------------------- | -------------------------- | ---------------- |
| `@modelcontextprotocol/server-filesystem`   | Read/write local files     | Local filesystem |
| `@modelcontextprotocol/server-github`       | GitHub repository access   | GitHub API       |
| `@modelcontextprotocol/server-slack`        | Slack workspace access     | Slack API        |
| `@modelcontextprotocol/server-postgres`     | PostgreSQL database access | PostgreSQL       |
| `@modelcontextprotocol/server-google-drive` | Google Drive files         | Google Drive API |
| `@modelcontextprotocol/server-puppeteer`    | Browser automation         | Headless Chrome  |

---

## Building Your First Agent

### Anatomy of a Minimal Agent

```
┌─────────────────────────────────────────────────────────────────┐
│              MINIMAL AGENT ARCHITECTURE                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  def agent(user_goal, tools, max_iterations=10):                │
│      messages = [system_prompt, user_goal]                       │
│      for i in range(max_iterations):                            │
│          # REASON: LLM decides next action                      │
│          response = llm.generate(messages)                       │
│                                                                  │
│          if response.has_tool_call:                              │
│              # ACT: Execute the tool                             │
│              result = execute_tool(response.tool_call)           │
│              # OBSERVE: Add result to conversation               │
│              messages.append(tool_result(result))                │
│          else:                                                   │
│              # DONE: Return final answer                         │
│              return response.content                             │
│                                                                  │
│      return "Max iterations reached. Partial result: ..."        │
│                                                                  │
│  KEY COMPONENTS:                                                 │
│  1. System Prompt — defines agent role and capabilities          │
│  2. Tool Definitions — what the agent can do                     │
│  3. ReAct Loop — think → act → observe → repeat                 │
│  4. Termination — know when to stop                              │
│  5. Error Handling — graceful failure                             │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Framework Comparison

| Framework             | Creator      | Strengths                                   | Best For                             |
| --------------------- | ------------ | ------------------------------------------- | ------------------------------------ |
| **LangGraph**         | LangChain    | Stateful graphs, persistence, human-in-loop | Production agents with complex state |
| **smolagents**        | Hugging Face | Lightweight, code-based agents              | Simple agents, learning              |
| **CrewAI**            | CrewAI       | Multi-agent roles and collaboration         | Team-of-agents scenarios             |
| **AutoGen**           | Microsoft    | Multi-agent conversations                   | Research, conversational agents      |
| **OpenAI Assistants** | OpenAI       | Built-in tools (code, retrieval)            | GPT-powered applications             |
| **Claude Code**       | Anthropic    | Single-threaded master loop, safety         | Coding agents                        |
| **PydanticAI**        | Pydantic     | Type-safe, structured outputs               | Type-safe agent development          |

---

## Study Questions & Discussion Prompts

### Conceptual Questions

1. **Definition Challenge:** In your own words, explain what makes an AI system "agentic." What are the minimum requirements for something to be considered an AI agent?

2. **Paradigm Shift:** How does the shift from "AI as a tool" (traditional LLM) to "AI as an agent" change the relationship between humans and AI systems? What new responsibilities emerge?

3. **ReAct Reasoning:** Walk through how a ReAct agent would handle this task: "Book the cheapest flight from New York to London for next Friday." List the thought-action-observation steps.

4. **Rational Agents:** Explain the difference between a goal-based agent and a utility-based agent. When would you prefer one over the other?

5. **Workflow vs. Agent:** When should you use a predefined workflow vs. a fully autonomous agent? Give examples of tasks suited to each approach.

### Applied Questions

6. **MCP Design:** Design an MCP server for a university system. What resources, tools, and prompts would you expose? Consider student records, course catalogs, and grade management.

7. **Workflow Selection:** You're building a customer support system that handles billing inquiries, technical issues, and general questions. Which agentic workflow pattern(s) would you use? Justify your choice.

8. **Agent Comparison:** Compare how a simple reflex agent vs. a learning agent would handle the task of email spam filtering. What capabilities does each have?

### Critical Analysis

9. **Limitations:** What are the current limitations of agentic AI? Identify at least three challenges that prevent fully autonomous agents from being deployed widely today.

10. **MCP Debate:** The Model Context Protocol standardizes agent-tool communication. Argue for and against standardization vs. proprietary tool interfaces. What are the trade-offs?

---

## Resources & References

### 📜 Key Papers

| #   | Paper                                              | Authors                | Link                             |
| --- | -------------------------------------------------- | ---------------------- | -------------------------------- |
| 1   | ReAct: Synergizing Reasoning and Acting in LLMs    | Yao et al.             | https://arxiv.org/abs/2210.03629 |
| 2   | Chain-of-Thought Prompting Elicits Reasoning       | Wei et al. (Google)    | https://arxiv.org/abs/2201.11903 |
| 3   | Tree of Thoughts: Deliberate Problem Solving       | Yao et al.             | https://arxiv.org/abs/2305.10601 |
| 4   | Toolformer: LLMs Can Teach Themselves to Use Tools | Schick et al. (Meta)   | https://arxiv.org/abs/2302.04761 |
| 5   | Generative Agents: Interactive Simulacra           | Park et al. (Stanford) | https://arxiv.org/abs/2304.03442 |

### 🗺️ Official Guides

| #   | Resource                                     | Link                                                                                          |
| --- | -------------------------------------------- | --------------------------------------------------------------------------------------------- |
| 1   | Anthropic: Building Effective Agents         | https://www.anthropic.com/engineering/building-effective-agents                               |
| 2   | OpenAI: A Practical Guide to Building Agents | https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf |
| 3   | Google: Agent Whitepaper                     | https://cloud.google.com/discover/what-are-ai-agents                                          |
| 4   | MCP Specification                            | https://modelcontextprotocol.io                                                               |
| 5   | MCP GitHub Repository                        | https://github.com/modelcontextprotocol                                                       |

### 🧑‍🏫 Courses

| #   | Course                                   | Provider        | Link                                                 |
| --- | ---------------------------------------- | --------------- | ---------------------------------------------------- |
| 1   | AI Agents for Beginners (Lessons 1-5)    | Microsoft       | https://github.com/microsoft/ai-agents-for-beginners |
| 2   | HuggingFace AI Agents Course (Units 1-2) | HuggingFace     | https://huggingface.co/learn/agents-course           |
| 3   | MCP: Build Rich-Context AI Apps          | DeepLearning.AI | https://www.deeplearning.ai/short-courses/           |
| 4   | Building Agents with MCP                 | Anthropic       | https://www.deeplearning.ai/short-courses/           |

### 📚 Books

| #   | Book                                                                     | Author(s)                     |
| --- | ------------------------------------------------------------------------ | ----------------------------- |
| 1   | _Artificial Intelligence: A Modern Approach_ (Ch. 2: Intelligent Agents) | Stuart Russell & Peter Norvig |
| 2   | _AI Agents: The Definitive Guide_                                        | Nicole Koenigstein            |
| 3   | _AI Agents with MCP_                                                     | Kyle Stratis                  |
| 4   | _Building Applications with AI Agents_                                   | Michael Albada                |

### 📹 Video Resources

| #   | Video                                 | Link                                        |
| --- | ------------------------------------- | ------------------------------------------- |
| 1   | Agentic AI Overview (Stanford)        | https://www.youtube.com/watch?v=kJLiOGle3Lw |
| 2   | Building Effective Agents (Anthropic) | https://www.youtube.com/watch?v=D7_ipDqhtwk |
| 3   | Building an Agent from Scratch        | https://www.youtube.com/watch?v=xzXdLRUyjUg |
| 4   | Building Agents with MCP              | https://www.youtube.com/watch?v=kQmXtrmQ5Zg |

---

## Key Takeaways

```
┌─────────────────────────────────────────────────────────────────┐
│              WEEK 6 — KEY TAKEAWAYS                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  1. AGENTIC AI IS A PARADIGM SHIFT                               │
│     From "prompt in, text out" to "goal in, results out."        │
│     Agents plan, act, observe, and adapt autonomously.           │
│                                                                  │
│  2. THE ReAct LOOP IS FOUNDATIONAL                               │
│     Think → Act → Observe → Repeat is the engine that           │
│     powers most modern AI agents.                                │
│                                                                  │
│  3. RATIONAL AGENTS BUILD ON CLASSICAL AI                        │
│     The Russell & Norvig agent taxonomy (simple reflex →         │
│     learning) maps directly to modern LLM-based agents.          │
│                                                                  │
│  4. WORKFLOWS BEFORE AGENTS                                      │
│     Start with predefined workflows. Add autonomy only           │
│     when the task requires dynamic decision-making.              │
│                                                                  │
│  5. MCP IS THE UNIVERSAL CONNECTOR                               │
│     The Model Context Protocol standardizes how agents           │
│     discover and use tools. Think of it as "USB-C for AI."       │
│                                                                  │
│  6. START SIMPLE, ITERATE                                        │
│     Simple LLM call → Workflow → Agent. Add complexity           │
│     only when simpler solutions aren't sufficient.               │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## Study Checklist

### Foundation (Days 1-2)

- [ ] Read Anthropic's "Building Effective Agents" guide
- [ ] Watch "Agentic AI Overview" (Stanford) video
- [ ] Study the five workflow patterns with examples
- [ ] Review the rational agent taxonomy (Russell & Norvig)

### Deep Dive (Days 3-4)

- [ ] Read the ReAct paper (Yao et al.)
- [ ] Explore MCP documentation at modelcontextprotocol.io
- [ ] Complete Microsoft AI Agents for Beginners Lessons 1-3
- [ ] Compare at least 3 agent frameworks (LangGraph, smolagents, CrewAI)

### Application (Days 5-6)

- [ ] Build a minimal ReAct agent from scratch (no framework)
- [ ] Set up and test an MCP server (filesystem or GitHub)
- [ ] Implement one workflow pattern (e.g., routing for a support bot)
- [ ] Experiment with a framework-based agent (LangGraph or smolagents)

### Synthesis (Day 7)

- [ ] Complete all study questions
- [ ] Write a comparison essay: "When to use workflows vs. autonomous agents"
- [ ] Design an agentic system for a real-world problem
- [ ] Present your findings to peers

---

_Last Updated: February 2026_
_Part of the AI Agents Comprehensive Study Guide Series_
_Compiled from official documentation, research papers, and industry resources_
