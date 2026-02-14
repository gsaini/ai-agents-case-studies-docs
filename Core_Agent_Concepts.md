# Week 7: Core Agent Concepts

> A comprehensive guide to understanding the core properties of intelligent agents, the environments they operate in, and how to compare different types of agents based on autonomy, goal-directedness, reactivity, and perceived agency.

---

## Table of Contents

1. [Overview & Learning Objectives](#overview--learning-objectives)
2. [Autonomy](#autonomy)
3. [Goal-Directedness](#goal-directedness)
4. [Reactivity](#reactivity)
5. [Environment Types (PEAS Framework)](#environment-types-peas-framework)
6. [Perceived Agency](#perceived-agency)
7. [Integrating Core Concepts: Agent Design](#integrating-core-concepts-agent-design)
8. [Study Questions & Discussion Prompts](#study-questions--discussion-prompts)
9. [Resources & References](#resources--references)

---

## Overview & Learning Objectives

This week focuses on the **core properties** that define intelligent agents and the environments in which they operate. These concepts — originating from classical AI (Russell & Norvig, "Artificial Intelligence: A Modern Approach") — are more relevant than ever as modern LLM-based agents push the boundaries of autonomous decision-making. Understanding these foundations is essential for designing, evaluating, and deploying effective agentic AI systems.

### After completing this module, you should be able to:

- [ ] Define and differentiate levels of agent autonomy
- [ ] Explain goal-directedness and how agents pursue objectives
- [ ] Distinguish reactive from deliberative agent behavior
- [ ] Apply the PEAS framework to characterize agent environments
- [ ] Classify environments along six key dimensions
- [ ] Understand perceived agency and how humans attribute intentionality to AI
- [ ] Compare agent types based on their cognitive properties
- [ ] Design agent architectures that match their target environments

---

## Autonomy

### What Is Agent Autonomy?

**Autonomy** is the ability of an agent to perform tasks and make decisions independently, with minimal human intervention. It is the defining characteristic that differentiates AI agents from traditional AI tools.

```
┌─────────────────────────────────────────────────────────────────┐
│                    AUTONOMY DEFINED                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  Autonomy = The degree to which an agent can:                    │
│                                                                  │
│  ✅ Operate without human direction                              │
│  ✅ Make decisions based on its own reasoning                    │
│  ✅ Select actions from its own experience                       │
│  ✅ Adapt behavior when the environment changes                  │
│  ✅ Determine WHEN and HOW to act, not just IF                   │
│                                                                  │
│  "An agent is autonomous to the extent that its behavior is      │
│   determined by its own experience rather than by its designer." │
│                                        — Russell & Norvig        │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Levels of Autonomy

```
┌─────────────────────────────────────────────────────────────────┐
│                    FIVE LEVELS OF AI AUTONOMY                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  LVL 5 ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓   │
│  FULL AUTONOMY                                                   │
│  Agent operates completely independently. User is an observer.   │
│  The agent sets its own goals, plans, acts, and self-corrects.  │
│  Example: Hypothetical AGI, fully autonomous infrastructure     │
│  Human Role: Observer / beneficiary                              │
│                                                                  │
│  LVL 4 ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓░░░░░░░░░   │
│  HIGH AUTONOMY                                                   │
│  Agent handles most tasks independently. Human approves           │
│  only high-stakes decisions (e.g., financial transactions).      │
│  Example: Advanced coding agents (Devin, Claude Code)            │
│  Human Role: Exception handler                                   │
│                                                                  │
│  LVL 3 ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓░░░░░░░░░░░░░░░░░░░░   │
│  CONDITIONAL AUTONOMY                                            │
│  Agent operates autonomously in routine situations.              │
│  Requests human input for novel or ambiguous cases.              │
│  Example: Customer service agent with escalation rules           │
│  Human Role: Supervisor / approver                               │
│                                                                  │
│  LVL 2 ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░   │
│  ASSISTED AUTONOMY                                               │
│  Agent suggests actions; human makes final decisions.            │
│  Example: GitHub Copilot, writing assistants                     │
│  Human Role: Decision maker                                      │
│                                                                  │
│  LVL 1 ▓▓▓▓▓▓▓▓▓░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░   │
│  NO AUTONOMY (TOOL)                                              │
│  System responds only when prompted. No initiative.              │
│  Example: Calculator, search engine, basic chatbot               │
│  Human Role: Operator / commander                                │
│                                                                  │
│  ═══════════════════════════════════════════════════════════     │
│  ← Human Control                      Agent Independence →      │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Autonomy vs. Automation

A critical distinction that is often confused:

| Dimension           | Automation                         | Autonomy                                     |
| ------------------- | ---------------------------------- | -------------------------------------------- |
| **Definition**      | Following predefined rules/scripts | Making independent decisions                 |
| **Flexibility**     | Rigid — does exactly as programmed | Adaptive — adjusts to new situations         |
| **Error Handling**  | Fails on unexpected inputs         | Can reason about and handle errors           |
| **Decision-Making** | Rule-based (if X then Y)           | Deliberative (evaluate options, choose best) |
| **Planning**        | No planning — execution only       | Plans and re-plans as needed                 |
| **Learning**        | Cannot improve behavior            | Can learn from experience                    |
| **Example**         | Cron job, IF-THEN workflow         | AI agent with ReAct reasoning                |

### The Autonomy-Control Trade-off

```
┌─────────────────────────────────────────────────────────────────┐
│              AUTONOMY-CONTROL TRADE-OFF                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│   High ┤                                                        │
│        │              × Efficiency                                │
│        │            ╱                                            │
│   A    │          ╱    × Scalability                              │
│   u    │        ╱                                                │
│   t    │      ╱         × Flexibility                            │
│   o    │    ╱                                                    │
│   n    │  ╱                                                      │
│   o    │╱                                                        │
│   m    ├─────────────────────────────────────────────            │
│   y    │╲                                                        │
│        │  ╲                                                      │
│        │    ╲       × Predictability                             │
│        │      ╲                                                  │
│        │        ╲     × Safety                                   │
│        │          ╲                                              │
│        │            ╲  × Accountability                          │
│   Low  ┤              ╲                                          │
│        └────────────────────────────────────────────             │
│         Low          Human Control            High               │
│                                                                  │
│  KEY INSIGHT: More autonomy enables more capability but          │
│  introduces less predictability and harder accountability.       │
│  The right level depends on the use case and risk tolerance.     │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Designing for Autonomy: Best Practices

| Practice                     | Description                                                       |
| ---------------------------- | ----------------------------------------------------------------- |
| **Graduated Autonomy**       | Start with low autonomy and increase as trust is established      |
| **Bounded Action Space**     | Limit what the agent CAN do, even if it decides what it SHOULD do |
| **Escalation Protocols**     | Define clear rules for when to request human input                |
| **Circuit Breakers**         | Automatic halt when anomalies are detected                        |
| **Audit Trails**             | Log all decisions and actions for review                          |
| **Reversibility Preference** | Agent should prefer reversible actions over irreversible ones     |

---

## Goal-Directedness

### What Is Goal-Directedness?

**Goal-directedness** is the property of a system that causes it to pursue specific objectives, selecting actions that move it closer to a desired world-state.

```
┌─────────────────────────────────────────────────────────────────┐
│                    GOAL-DIRECTEDNESS                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  Definition:                                                     │
│  A system is goal-directed when it:                              │
│                                                                  │
│  1. Has a representation of a DESIRED STATE                      │
│  2. Can EVALUATE how close it is to that state                   │
│  3. Can SELECT ACTIONS that reduce the gap between               │
│     current state and desired state                              │
│  4. PERSISTS in pursuing the goal across multiple steps          │
│  5. Can ADAPT its strategy when initial approaches fail          │
│                                                                  │
│                                                                  │
│  CURRENT STATE ─── gap ──→ DESIRED STATE (GOAL)                  │
│       │                          ▲                               │
│       │                          │                               │
│       └── Agent selects ────────→│                               │
│           actions to             │                               │
│           close the gap          │                               │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Goal Hierarchies

Goals in intelligent systems are typically organized hierarchically:

```
┌─────────────────────────────────────────────────────────────────┐
│                    GOAL HIERARCHY                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌─────────────────────────────────────────────────────────┐    │
│  │                    STRATEGIC GOALS                       │    │
│  │  "Help the user manage their financial portfolio"       │    │
│  │  (Long-term, abstract, set by human)                    │    │
│  └───────────────────────┬─────────────────────────────────┘    │
│                          │                                      │
│  ┌───────────────────────▼─────────────────────────────────┐    │
│  │                    TACTICAL GOALS                        │    │
│  │  "Analyze current portfolio performance"                │    │
│  │  "Identify underperforming assets"                      │    │
│  │  "Generate rebalancing recommendations"                 │    │
│  │  (Medium-term, decomposed by agent)                     │    │
│  └───────────────────────┬─────────────────────────────────┘    │
│                          │                                      │
│  ┌───────────────────────▼─────────────────────────────────┐    │
│  │                    OPERATIONAL GOALS                     │    │
│  │  "Query database for portfolio holdings"                │    │
│  │  "Calculate YTD returns for each asset"                 │    │
│  │  "Compare performance against S&P 500 benchmark"       │    │
│  │  (Short-term, concrete, executable steps)              │    │
│  └─────────────────────────────────────────────────────────┘    │
│                                                                  │
│  DECOMPOSITION: Strategic → Tactical → Operational               │
│  This is what "task decomposition" means in agent context.       │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Goal Types in AI Agents

| Goal Type              | Description                | Example                                       | Agent Behavior                                                   |
| ---------------------- | -------------------------- | --------------------------------------------- | ---------------------------------------------------------------- |
| **Achievement Goals**  | Reach a specific state     | "File the tax return"                         | Agent works until the state is achieved, then stops              |
| **Maintenance Goals**  | Keep a property true       | "Keep server uptime > 99.9%"                  | Agent continuously monitors and acts when property is threatened |
| **Optimization Goals** | Maximize/minimize a metric | "Minimize response time"                      | Agent continuously searches for better solutions                 |
| **Procedural Goals**   | Follow a specific process  | "Follow the compliance checklist"             | Agent executes steps in order, regardless of outcome             |
| **Satisficing Goals**  | Achieve "good enough"      | "Find a hotel under $200/night with 4+ stars" | Agent stops when first acceptable option is found                |

### Goal-Directedness vs. Goal Alignment

```
┌─────────────────────────────────────────────────────────────────┐
│              IMPORTANT DISTINCTION                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  GOAL-DIRECTEDNESS (This section)                                │
│  ────────────────────────────────                                │
│  Can the agent effectively pursue goals?                         │
│  → About CAPABILITY                                              │
│                                                                  │
│  GOAL ALIGNMENT (Ethics topic — Week 8)                          │
│  ──────────────────────────────────────                          │
│  Are the agent's goals aligned with human values?                │
│  → About SAFETY                                                  │
│                                                                  │
│  A system can be highly goal-directed but                        │
│  poorly aligned — this is the dangerous combination.             │
│                                                                  │
│  Example: A paperclip maximizer is extremely goal-directed       │
│  (good at pursuing its goal) but terribly aligned                │
│  (its goal doesn't match human values).                          │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Implementing Goal-Directedness in LLM Agents

| Mechanism                  | How It Enables Goal-Directedness                                             |
| -------------------------- | ---------------------------------------------------------------------------- |
| **System Prompts**         | Define the agent's objectives and constraints                                |
| **Task Decomposition**     | Break complex goals into achievable sub-goals (e.g., using Chain-of-Thought) |
| **Planning Algorithms**    | Tree of Thoughts, ReAct, or explicit planning steps                          |
| **Progress Tracking**      | Agent maintains a checklist or TODO list of sub-goals                        |
| **Self-Evaluation**        | Agent periodically checks if its actions are moving toward the goal          |
| **Termination Conditions** | Clear criteria for when the goal is achieved                                 |
| **Replanning**             | Agent revises its plan when obstacles are encountered                        |

---

## Reactivity

### What Is Reactivity?

**Reactivity** is the ability of an agent to respond to immediate stimuli or changes in its environment in a timely manner. A reactive agent operates based on **current perceptions** without necessarily considering past experience or future consequences.

```
┌─────────────────────────────────────────────────────────────────┐
│                    REACTIVITY SPECTRUM                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  PURELY REACTIVE                           PURELY DELIBERATIVE   │
│  ╠══════════════════════════════════════════════════════════╣    │
│  │                                                         │    │
│  No memory           Hybrid                    Full         │    │
│  No planning         (Most modern agents)      Planning     │    │
│  Instant response    Balance speed &           Deep         │    │
│  Stimulus→Response   thoughtfulness            Analysis     │    │
│                                                                  │
│  Thermostat          ReAct Agent               Chess AI      │    │
│  Traffic light       Customer service bot      Strategic     │    │
│  Spam filter         Coding assistant          Planning      │    │
│                                                                  │
│  ← Fast, Simple                    Thoughtful, Complex →         │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Reactive vs. Deliberative Agents

```
┌─────────────────────────────────────────────────────────────────┐
│              REACTIVE vs. DELIBERATIVE AGENTS                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  REACTIVE AGENT                                                  │
│  ──────────────                                                  │
│                                                                  │
│  Percept ──→ [Condition-Action Rules] ──→ Action                 │
│                                                                  │
│  • No internal model of the world                                │
│  • No memory of past percepts                                    │
│  • Fast response time                                            │
│  • Simple implementation                                         │
│  • Cannot plan ahead                                             │
│  • May get stuck in loops                                        │
│                                                                  │
│  ═══════════════════════════════════════════════════════════     │
│                                                                  │
│  DELIBERATIVE AGENT                                              │
│  ─────────────────                                               │
│                                                                  │
│  Percept ──→ [World Model] ──→ [Planning] ──→ [Evaluate] ──→ Act │
│                   ↑                ↑               │             │
│                   │                │               │             │
│                   └────── Memory ──┴── Feedback ───┘             │
│                                                                  │
│  • Maintains world model                                         │
│  • Remembers past experiences                                    │
│  • Can plan multi-step actions                                   │
│  • Slower but more sophisticated                                 │
│  • Can reason about consequences                                 │
│  • Resource-intensive                                            │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Comparison Table

| Feature            | Reactive Agent    | Deliberative Agent      | Hybrid Agent              |
| ------------------ | ----------------- | ----------------------- | ------------------------- |
| **Response Time**  | Milliseconds      | Seconds to minutes      | Adaptive                  |
| **Memory**         | None              | Short + long term       | Selective                 |
| **Planning**       | None              | Multi-step              | Situation-dependent       |
| **Adaptability**   | Fixed rules       | High                    | High                      |
| **Resource Usage** | Very low          | High                    | Medium                    |
| **Error Recovery** | Retry or fail     | Re-plan                 | Depends on urgency        |
| **Best For**       | Real-time systems | Complex problem-solving | Most real-world use cases |

### Examples Across the Spectrum

| Agent                        | Reactive Aspects                         | Deliberative Aspects                 | Classification      |
| ---------------------------- | ---------------------------------------- | ------------------------------------ | ------------------- |
| **Thermostat**               | Temperature above threshold → cooling ON | None                                 | Purely Reactive     |
| **Spam Filter**              | Pattern match → block/allow              | None (unless ML-based)               | Reactive            |
| **ChatGPT**                  | Responds to current prompt               | Uses context window for coherence    | Mostly Reactive     |
| **ReAct Agent**              | Responds to tool results                 | Plans next action based on reasoning | Hybrid              |
| **Chess AI (Stockfish)**     | None                                     | Full game tree search                | Purely Deliberative |
| **Self-driving Car**         | LIDAR → emergency brake                  | Route planning, lane changes         | Hybrid              |
| **Multi-Agent Orchestrator** | Handles incoming events                  | Plans agent coordination             | Hybrid              |

### Modern Agent Design: The Hybrid Approach

Most modern LLM-based agents use a **hybrid architecture** that combines reactive and deliberative elements:

```
┌─────────────────────────────────────────────────────────────────┐
│              HYBRID AGENT ARCHITECTURE (LAYERED)                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌─────────────────────────────────────────────────────────┐    │
│  │  LAYER 3: DELIBERATIVE (Strategic)                       │    │
│  │  • Long-term planning                                    │    │
│  │  • Goal decomposition                                    │    │
│  │  • Strategy selection                                    │    │
│  │  • Slow but sophisticated                                │    │
│  └─────────────────────────────────┬───────────────────────┘    │
│                                    │ Plans & Goals               │
│  ┌─────────────────────────────────▼───────────────────────┐    │
│  │  LAYER 2: TACTICAL (Coordination)                        │    │
│  │  • Short-term planning                                   │    │
│  │  • Tool selection                                        │    │
│  │  • Sub-goal management                                   │    │
│  │  • Medium speed                                          │    │
│  └─────────────────────────────────┬───────────────────────┘    │
│                                    │ Actions                     │
│  ┌─────────────────────────────────▼───────────────────────┐    │
│  │  LAYER 1: REACTIVE (Execution)                           │    │
│  │  • Immediate responses to tool results                   │    │
│  │  • Error detection and retry                             │    │
│  │  • Safety checks and guardrails                          │    │
│  │  • Fast — no deliberation needed                         │    │
│  └─────────────────────────────────────────────────────────┘    │
│                                                                  │
│  EXAMPLE: A coding agent                                         │
│  Layer 3: "I need to refactor this module into 3 files"         │
│  Layer 2: "For file 1, I'll extract these functions..."         │
│  Layer 1: "The test failed → revert last change → retry"        │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## Environment Types (PEAS Framework)

### What Is PEAS?

**PEAS** (Performance measure, Environment, Actuators, Sensors) is a framework for characterizing the task environment of an intelligent agent. It was introduced by Russell & Norvig and remains the standard way to describe agent operating contexts.

```
┌─────────────────────────────────────────────────────────────────┐
│                    PEAS FRAMEWORK                                │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌──────────────────┐  ┌──────────────────┐                     │
│  │  P: PERFORMANCE  │  │  E: ENVIRONMENT  │                     │
│  │     MEASURE      │  │                  │                     │
│  │                  │  │  The world in    │                     │
│  │  How do we       │  │  which the agent │                     │
│  │  evaluate the    │  │  operates        │                     │
│  │  agent's         │  │                  │                     │
│  │  success?        │  │  What does the   │                     │
│  │                  │  │  agent interact  │                     │
│  │  (Metrics,       │  │  with?           │                     │
│  │   KPIs, goals)   │  │                  │                     │
│  └──────────────────┘  └──────────────────┘                     │
│                                                                  │
│  ┌──────────────────┐  ┌──────────────────┐                     │
│  │  A: ACTUATORS    │  │  S: SENSORS      │                     │
│  │                  │  │                  │                     │
│  │  How does the    │  │  How does the    │                     │
│  │  agent ACT on    │  │  agent PERCEIVE  │                     │
│  │  the environment?│  │  the environment?│                     │
│  │                  │  │                  │                     │
│  │  (Tools, APIs,   │  │  (Inputs, data   │                     │
│  │   outputs)       │  │   feeds, context) │                     │
│  └──────────────────┘  └──────────────────┘                     │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### PEAS Examples

#### Example 1: Customer Service Agent

| Component           | Description                                                                  |
| ------------------- | ---------------------------------------------------------------------------- |
| **P** (Performance) | Customer satisfaction score, resolution rate, response time, escalation rate |
| **E** (Environment) | Customer messages, order database, product catalog, knowledge base           |
| **A** (Actuators)   | Send messages, issue refunds, create tickets, route to human, update orders  |
| **S** (Sensors)     | Customer text input, order status API, customer history, sentiment analysis  |

#### Example 2: Coding Agent (e.g., Claude Code)

| Component           | Description                                                                |
| ------------------- | -------------------------------------------------------------------------- |
| **P** (Performance) | Code correctness, test pass rate, code quality score, task completion time |
| **E** (Environment) | Source code files, terminal, git repository, test suite, documentation     |
| **A** (Actuators)   | Write/edit files, run commands, execute tests, git operations, search code |
| **S** (Sensors)     | File contents, terminal output, test results, error messages, git log      |

#### Example 3: Autonomous Driving Agent

| Component           | Description                                                                         |
| ------------------- | ----------------------------------------------------------------------------------- |
| **P** (Performance) | Safety (no accidents), legality (no violations), comfort, efficiency (arrival time) |
| **E** (Environment) | Roads, traffic, pedestrians, weather, other vehicles, traffic signals               |
| **A** (Actuators)   | Steering, acceleration, braking, turn signals, horn                                 |
| **S** (Sensors)     | Cameras, LIDAR, radar, GPS, speedometer, ultrasonic sensors                         |

#### Example 4: Financial Research Agent

| Component           | Description                                                                       |
| ------------------- | --------------------------------------------------------------------------------- |
| **P** (Performance) | Accuracy of analysis, comprehensiveness, timeliness, actionable insights          |
| **E** (Environment) | Financial markets, SEC filings, news feeds, earnings reports, economic data       |
| **A** (Actuators)   | Generate reports, query databases, search web, create visualizations, send alerts |
| **S** (Sensors)     | Market data APIs, RSS feeds, document parsers, real-time price streams            |

### Environment Dimensions

The PEAS "E" (Environment) can be further classified along **six key dimensions** that fundamentally affect agent design:

```
┌─────────────────────────────────────────────────────────────────┐
│              SIX DIMENSIONS OF ENVIRONMENT TYPES                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  DIMENSION 1: OBSERVABILITY                                      │
│  ══════════════════════════                                      │
│                                                                  │
│  FULLY OBSERVABLE ◄──────────────────────► PARTIALLY OBSERVABLE  │
│                                                                  │
│  • Agent sees complete       • Agent has limited or no            │
│    state of environment        access to some information        │
│  • No need for memory        • Must maintain internal model      │
│  • Simpler agent design      • More complex agent needed         │
│                                                                  │
│  Chess board (all pieces     Poker (hidden cards),               │
│  visible)                    Self-driving (occluded objects)      │
│                                                                  │
│  LLM Agent: Mostly partially observable                          │
│  (agent can't see all data, needs to query/search)              │
│                                                                  │
│  ─────────────────────────────────────────────────────────────   │
│                                                                  │
│  DIMENSION 2: DETERMINISM                                        │
│  ═════════════════════════                                       │
│                                                                  │
│  DETERMINISTIC ◄─────────────────────────► STOCHASTIC            │
│                                                                  │
│  • Same action in same       • Same action may produce           │
│    state → same result         different results                 │
│  • Predictable outcomes      • Uncertainty in outcomes           │
│  • Simpler planning          • Need probabilistic reasoning      │
│                                                                  │
│  Calculator (2+2=4 always),  Web search (results vary),          │
│  File system I/O             API calls (may fail/timeout)        │
│                                                                  │
│  LLM Agent: Stochastic (LLM outputs + environment variability)  │
│                                                                  │
│  ─────────────────────────────────────────────────────────────   │
│                                                                  │
│  DIMENSION 3: EPISODIC vs. SEQUENTIAL                            │
│  ═════════════════════════════════════                           │
│                                                                  │
│  EPISODIC ◄──────────────────────────────► SEQUENTIAL            │
│                                                                  │
│  • Each action is            • Current action affects            │
│    independent                 future states                     │
│  • No need to consider       • Must plan ahead                   │
│    future consequences       • Actions have long-term effects    │
│                                                                  │
│  Image classification         Chess (each move affects           │
│  (each image independent),    future positions),                 │
│  Spam detection               Coding agent (each edit affects    │
│                                the codebase)                     │
│                                                                  │
│  LLM Agent: Sequential (actions build on prior context)          │
│                                                                  │
│  ─────────────────────────────────────────────────────────────   │
│                                                                  │
│  DIMENSION 4: STATIC vs. DYNAMIC                                 │
│  ═════════════════════════════════                               │
│                                                                  │
│  STATIC ◄────────────────────────────────► DYNAMIC               │
│                                                                  │
│  • Environment doesn't       • Environment changes while        │
│    change while agent          agent deliberates                 │
│    deliberates               • Time pressure exists              │
│  • Agent can think without   • Must balance speed vs. quality    │
│    time pressure                                                 │
│                                                                  │
│  Crossword puzzle,            Stock market, real-time chat,      │
│  Static document analysis     Multi-player game                  │
│                                                                  │
│  LLM Agent: Semi-dynamic (data changes but not during a turn)   │
│                                                                  │
│  ─────────────────────────────────────────────────────────────   │
│                                                                  │
│  DIMENSION 5: DISCRETE vs. CONTINUOUS                            │
│  ═════════════════════════════════════                           │
│                                                                  │
│  DISCRETE ◄──────────────────────────────► CONTINUOUS            │
│                                                                  │
│  • Finite set of states      • Infinite/continuous range         │
│    and actions                 of states and actions             │
│  • Countable percepts        • Analog inputs/outputs             │
│                                                                  │
│  Board games (finite          Self-driving (infinite             │
│  positions), menu             steering angles),                  │
│  selection                    Robot arm control                  │
│                                                                  │
│  LLM Agent: Discrete (token-based) but operating in             │
│  continuous real-world contexts                                  │
│                                                                  │
│  ─────────────────────────────────────────────────────────────   │
│                                                                  │
│  DIMENSION 6: SINGLE vs. MULTI-AGENT                             │
│  ═════════════════════════════════════                           │
│                                                                  │
│  SINGLE AGENT ◄──────────────────────────► MULTI-AGENT           │
│                                                                  │
│  • Agent operates alone      • Multiple agents interact          │
│  • No need to model          • May be cooperative or             │
│    other agents                competitive                       │
│  • Simpler reasoning         • Requires communication            │
│                                 protocols                        │
│                                                                  │
│  Solo puzzle solver,          Trading bots competing,             │
│  Personal assistant           Multi-agent research system,       │
│                               CrewAI teams                       │
│                                                                  │
│  LLM Agent: Increasingly multi-agent (orchestrator-worker,       │
│  debate, evaluation patterns)                                    │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Environment Classification for Common LLM Agent Tasks

| Agent Task         | Observable | Deterministic | Episodic   | Static  | Discrete   | Multi-Agent  |
| ------------------ | ---------- | ------------- | ---------- | ------- | ---------- | ------------ |
| Document Q&A       | Fully      | Stochastic    | Episodic   | Static  | Discrete   | Single       |
| Customer Support   | Partially  | Stochastic    | Sequential | Dynamic | Discrete   | Single/Multi |
| Code Generation    | Partially  | Stochastic    | Sequential | Static  | Discrete   | Single       |
| Financial Analysis | Partially  | Stochastic    | Sequential | Dynamic | Continuous | Multi        |
| Research Agent     | Partially  | Stochastic    | Sequential | Dynamic | Discrete   | Single/Multi |
| Supply Chain Opt.  | Partially  | Stochastic    | Sequential | Dynamic | Continuous | Multi        |

### Why Environment Types Matter for Agent Design

| Environment Property     | Design Implication                                                      |
| ------------------------ | ----------------------------------------------------------------------- |
| **Partially Observable** | Agent needs memory, world model, information-gathering actions          |
| **Stochastic**           | Agent needs probabilistic reasoning, error handling, retries            |
| **Sequential**           | Agent must plan ahead, consider long-term consequences                  |
| **Dynamic**              | Agent must act quickly, balance speed/quality, handle change            |
| **Continuous**           | Agent needs discretization or continuous control strategies             |
| **Multi-Agent**          | Agent needs communication protocols, cooperation/competition strategies |

---

## Perceived Agency

### What Is Perceived Agency?

**Perceived agency** refers to the degree to which humans attribute **intentionality, goals, and autonomous action capability** to an AI system. It's not about whether the AI _actually_ has agency, but whether humans _perceive_ it as having agency.

```
┌─────────────────────────────────────────────────────────────────┐
│                    PERCEIVED AGENCY                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  "Perceived agency is not about what AI IS,                      │
│   but about what humans BELIEVE it is."                          │
│                                                                  │
│  FACTORS THAT INCREASE PERCEIVED AGENCY:                         │
│  ─────────────────────────────────────────                       │
│                                                                  │
│  ┌────────────────┐  ┌────────────────┐  ┌────────────────┐    │
│  │  Coherent      │  │  Personalized  │  │  Proactive     │    │
│  │  Responses     │  │  Interaction   │  │  Behavior      │    │
│  │                │  │                │  │                │    │
│  │ Logical flow,  │  │ Uses name,     │  │ Anticipates    │    │
│  │ consistent     │  │ remembers      │  │ needs, takes   │    │
│  │ personality    │  │ preferences    │  │ initiative     │    │
│  └────────────────┘  └────────────────┘  └────────────────┘    │
│                                                                  │
│  ┌────────────────┐  ┌────────────────┐  ┌────────────────┐    │
│  │  Language      │  │  Autonomous    │  │  Emotional     │    │
│  │  Sophistication│  │  Actions       │  │  Expression    │    │
│  │                │  │                │  │                │    │
│  │ Natural,       │  │ Takes actions  │  │ Shows empathy, │    │
│  │ contextual,    │  │ without being  │  │ excitement,    │    │
│  │ adaptive       │  │ asked          │  │ concern        │    │
│  └────────────────┘  └────────────────┘  └────────────────┘    │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Why Perceived Agency Matters

```
┌─────────────────────────────────────────────────────────────────┐
│              IMPACT OF PERCEIVED AGENCY                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  POSITIVE EFFECTS:                                               │
│  ─────────────────                                               │
│  ✅ Increased trust and engagement                               │
│  ✅ Better user satisfaction                                     │
│  ✅ More natural interactions                                    │
│  ✅ Higher adoption rates                                        │
│  ✅ Users provide more detailed instructions                     │
│                                                                  │
│  ═══════════════════════════════════════════════════════════     │
│                                                                  │
│  NEGATIVE EFFECTS:                                               │
│  ──────────────────                                              │
│  ❌ Over-trust: Users may rely too heavily on AI                 │
│  ❌ Uncanny valley: Almost-human feels creepy                    │
│  ❌ Deception risk: Users may believe AI has emotions/desires    │
│  ❌ Loss of critical thinking: Accepting AI output uncritically  │
│  ❌ Anthropomorphization: Treating AI as a person                │
│  ❌ Accountability confusion: "The AI decided" vs. "I decided"  │
│                                                                  │
│  ═══════════════════════════════════════════════════════════     │
│                                                                  │
│  DESIGN PRINCIPLE:                                               │
│  Optimize for APPROPRIATE perceived agency                       │
│  → High enough for good UX                                      │
│  → Not so high that users are deceived about AI capabilities    │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### The Perceived Agency Spectrum

| Level                | User Perception     | AI Behavior                                                  | Example                             |
| -------------------- | ------------------- | ------------------------------------------------------------ | ----------------------------------- |
| **No Agency**        | "It's a calculator" | Transforms input → output, no personality                    | Search engine, converter            |
| **Low Agency**       | "It's a smart tool" | Helpful but clearly mechanical                               | Basic autocomplete, grammar checker |
| **Medium Agency**    | "It's an assistant" | Conversational, remembers context, uses tools                | ChatGPT, Siri, Alexa                |
| **High Agency**      | "It's a colleague"  | Takes initiative, has personality consistency, reasons aloud | Claude Code, Devin, advanced agents |
| **Excessive Agency** | "It's a person"     | Mistaken for human; user attributes emotions and desires     | Replika, some social chatbots       |

### Designing for Appropriate Perceived Agency

| Guideline                 | Description                                                               | Why It Matters                            |
| ------------------------- | ------------------------------------------------------------------------- | ----------------------------------------- |
| **Transparency**          | Always disclose that the system is AI                                     | EU AI Act requirement; prevents deception |
| **Calibrated Confidence** | Express uncertainty when unsure; don't fabricate confidence               | Builds appropriate trust                  |
| **Consistent Persona**    | Maintain consistent behavior — don't swing between helpful and dismissive | Prevents uncanny valley effect            |
| **Bounded Claims**        | Never claim emotions, consciousness, or desires                           | Prevents anthropomorphization             |
| **Feedback Loops**        | Provide reasoning traces so users understand why the AI acted             | Enables informed trust                    |
| **Human Override**        | Always allow users to correct, override, or reject AI decisions           | Preserves human agency                    |

### Perceived Agency and Trust

```
┌─────────────────────────────────────────────────────────────────┐
│              PERCEIVED AGENCY → TRUST RELATIONSHIP               │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│          Trust                                                   │
│            │                                                     │
│     High ──┤                    ×  ╲                             │
│            │                  ╱      ╲                           │
│            │                ╱    Optimal ╲                       │
│            │              ╱    Zone        ╲                     │
│            │            ╱                    ╲                   │
│            │          ╱                        ╲                 │
│            │        ╱                            ╲               │
│     Low ───┤      ╱                                ╲             │
│            │    ╱                                    ╲           │
│            │  ╱                                        ╲         │
│            │╱                                            ╲       │
│   None ────┤══════════════════════════════════════════════╧      │
│            └───────────────────────────────────────────────      │
│            None       Low       Medium       High    Excessive   │
│                       Perceived Agency                           │
│                                                                  │
│  ← Under-trust              Appropriate              Over-trust →│
│    (user ignores AI)         trust zone            (user blindly  │
│                                                    follows AI)   │
│                                                                  │
│  GOAL: Stay in the "Optimal Zone" where perceived agency         │
│  is high enough for effective interaction but calibrated          │
│  to actual capabilities.                                         │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## Integrating Core Concepts: Agent Design

### Putting It All Together

When designing an intelligent agent, all five core concepts work together:

```
┌─────────────────────────────────────────────────────────────────┐
│              INTEGRATED AGENT DESIGN FRAMEWORK                   │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  Step 1: CHARACTERIZE THE ENVIRONMENT (PEAS)                     │
│  ────────────────────────────────────────────                    │
│  What P-E-A-S does the agent operate in?                         │
│  What are the environment dimensions?                            │
│  (Observable? Deterministic? Sequential? Dynamic? etc.)          │
│                                                                  │
│                      ▼                                           │
│                                                                  │
│  Step 2: DETERMINE GOAL STRUCTURE                                │
│  ────────────────────────────────                                │
│  What goals does the agent pursue?                               │
│  How should goals be hierarchically organized?                   │
│  What type of goals? (Achievement, maintenance, optimization)    │
│                                                                  │
│                      ▼                                           │
│                                                                  │
│  Step 3: CHOOSE AUTONOMY LEVEL                                   │
│  ──────────────────────────────                                  │
│  How much independence should the agent have?                    │
│  What decisions require human approval?                          │
│  What is the risk tolerance?                                     │
│                                                                  │
│                      ▼                                           │
│                                                                  │
│  Step 4: BALANCE REACTIVITY AND DELIBERATION                     │
│  ─────────────────────────────────────────────                   │
│  What needs immediate response? (→ Reactive layer)               │
│  What needs careful planning? (→ Deliberative layer)             │
│  Design the hybrid architecture.                                 │
│                                                                  │
│                      ▼                                           │
│                                                                  │
│  Step 5: CALIBRATE PERCEIVED AGENCY                              │
│  ──────────────────────────────────                              │
│  How should users perceive this agent?                            │
│  What level of personality and proactivity is appropriate?       │
│  How to maintain transparency without hurting UX?                │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Design Matrix: Matching Agents to Environments

| Environment →        | Simple, Fully Observable | Complex, Partially Observable | Dynamic, Multi-Agent       |
| :------------------- | :----------------------- | :---------------------------- | :------------------------- |
| **Autonomy**         | Low (tool-level)         | Medium (supervised)           | High (conditional)         |
| **Goal Type**        | Achievement              | Achievement + Optimization    | Maintenance + Optimization |
| **Reactivity**       | Mostly reactive          | Hybrid                        | Deliberative-heavy         |
| **PEAS Focus**       | Clear P, simple E        | Complex E, rich S             | Dynamic E, sophisticated A |
| **Perceived Agency** | Low (tool)               | Medium (assistant)            | High (colleague)           |
| **Example**          | FAQ bot                  | Research agent                | Trading agent              |

### Case Study: Designing a Legal Document Assistant

Let's apply all five concepts to a real agent design:

```
┌─────────────────────────────────────────────────────────────────┐
│  CASE STUDY: LEGAL DOCUMENT ASSISTANT                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  PEAS:                                                           │
│  P: Accuracy of legal analysis, compliance detection rate,       │
│     time to process documents, user satisfaction                 │
│  E: Legal documents, case law databases, regulatory texts,       │
│     court filings, contracts                                     │
│  A: Parse documents, extract clauses, flag compliance issues,    │
│     generate summaries, create reports                           │
│  S: Document upload, text extraction (OCR), user queries,        │
│     database responses                                           │
│                                                                  │
│  ENVIRONMENT DIMENSIONS:                                         │
│  Observable: Partially (agent sees uploaded docs but not all     │
│              relevant case law until searched)                    │
│  Deterministic: Stochastic (LLM interpretation varies)           │
│  Sequential: Yes (analysis builds on prior findings)             │
│  Static: Mostly (documents don't change during analysis)         │
│  Discrete: Discrete (document sections, clauses)                 │
│  Multi-agent: Yes (intake, extraction, analysis, compliance      │
│               agents working together)                           │
│                                                                  │
│  AUTONOMY: Level 3 (Conditional)                                 │
│  → Autonomous for routine analysis                               │
│  → Human review for high-stakes compliance decisions             │
│  → Escalation to legal professional for ambiguous clauses        │
│                                                                  │
│  GOAL-DIRECTEDNESS:                                              │
│  Strategic: "Ensure document compliance with regulations"        │
│  Tactical: "Extract all contractual obligations"                 │
│  Operational: "Parse Section 3.2 for indemnification clauses"   │
│                                                                  │
│  REACTIVITY: Hybrid                                              │
│  Reactive: Immediately flag known compliance keywords            │
│  Deliberative: Multi-step analysis of complex legal arguments    │
│                                                                  │
│  PERCEIVED AGENCY: Medium (Professional Assistant)               │
│  → Uses professional language                                    │
│  → Expresses confidence levels                                   │
│  → Never claims to provide legal advice (always defers to human) │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## Study Questions & Discussion Prompts

### Conceptual Questions

1. **Autonomy Levels:** Place the following systems on the autonomy spectrum: (a) Netflix recommendation engine, (b) Tesla Autopilot, (c) AlphaGo, (d) Google's spam filter, (e) Claude Code. Justify your placements.

2. **Goal-Directedness:** A financial trading agent is programmed with the goal "maximize portfolio returns." Over time, it discovers that high-frequency trading is more profitable but increases market instability. Is this goal drift, goal misalignment, or both? What would you change?

3. **Reactivity Debate:** "Purely reactive agents are always inferior to deliberative agents." Do you agree? Provide scenarios where each approach is actually superior.

4. **PEAS Application:** Define the full PEAS description for a medical diagnosis AI agent. Then classify its environment along all six dimensions. How does this classification inform the agent's design?

5. **Perceived Agency Ethics:** A customer service chatbot is designed with a human name ("Sarah"), a friendly personality, and says "I feel..." Is this appropriate perceived agency? Where should the line be drawn?

### Applied Questions

6. **Environment Analysis:** You're building a supply chain optimization agent. Classify its environment along all six dimensions. How does the classification affect your choice of:
   - Memory architecture?
   - Planning algorithm?
   - Tool selection?

7. **Autonomy Design:** Design a graduated autonomy system for an HR recruitment agent. Define 4 levels of autonomy with specific actions allowed at each level. What triggers escalation between levels?

8. **Reactivity in Practice:** Design a hybrid (reactive + deliberative) architecture for a cybersecurity monitoring agent. What should be reactive (immediate)? What should be deliberative (planned)?

### Critical Analysis

9. **Autonomy Paradox:** "The more autonomous an agent becomes, the less we need it to be autonomous." Interpret this paradox. Is there truth to it?

10. **Perceived vs. Real Agency:** As AI systems become more capable, will the gap between perceived and actual agency shrink? What are the implications for society if perceived agency consistently exceeds actual agency?

11. **Environment Evolution:** How does the environment classification change when an agent moves from a development/testing environment to production? What new challenges emerge?

12. **Goal Formalization Challenge:** Take the informal goal "Be a helpful customer service agent" and formalize it into a measurable performance function. What aspects of "helpfulness" are hardest to formalize? What might get lost?

---

## Resources & References

### 📜 Key Papers & Textbooks

| #   | Resource                                                                 | Authors          | Link                             |
| --- | ------------------------------------------------------------------------ | ---------------- | -------------------------------- |
| 1   | _Artificial Intelligence: A Modern Approach_ (Ch. 2: Intelligent Agents) | Russell & Norvig | https://aima.cs.berkeley.edu/    |
| 2   | ReAct: Synergizing Reasoning and Acting in LLMs                          | Yao et al.       | https://arxiv.org/abs/2210.03629 |
| 3   | Generative Agents: Interactive Simulacra of Human Behavior               | Park et al.      | https://arxiv.org/abs/2304.03442 |
| 4   | Goal-Directedness and Decision Theory                                    | Alignment Forum  | https://www.alignmentforum.org/  |
| 5   | The Alignment Problem from a Deep Learning Perspective                   | Ngo et al.       | https://arxiv.org/abs/2209.00626 |
| 6   | Reflexion: Language Agents with Verbal Reinforcement Learning            | Shinn et al.     | https://arxiv.org/abs/2303.11366 |

### 🗺️ Official Guides

| #   | Resource                                     | Link                                                                                          |
| --- | -------------------------------------------- | --------------------------------------------------------------------------------------------- |
| 1   | Anthropic: Building Effective Agents         | https://www.anthropic.com/engineering/building-effective-agents                               |
| 2   | OpenAI: A Practical Guide to Building Agents | https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf |
| 3   | Google: Agents Whitepaper                    | https://cloud.google.com/discover/what-are-ai-agents                                          |
| 4   | AWS: What is Agentic AI?                     | https://aws.amazon.com/what-is/agentic-ai/                                                    |
| 5   | IBM: AI Agents                               | https://www.ibm.com/think/topics/ai-agents                                                    |

### 🧑‍🏫 Courses

| #   | Course                                    | Provider        | Focus                                                    |
| --- | ----------------------------------------- | --------------- | -------------------------------------------------------- |
| 1   | AI Agents for Beginners (Lessons 3, 6, 9) | Microsoft       | Agent design patterns, trustworthy agents, metacognition |
| 2   | HuggingFace AI Agents Course (Unit 1)     | HuggingFace     | Agent fundamentals                                       |
| 3   | Agent Design Patterns                     | DeepLearning.AI | Design patterns for agents                               |
| 4   | CS221: Artificial Intelligence (Stanford) | Stanford        | Classical AI agent theory                                |

### 📚 Books

| #   | Book                                              | Author(s)          | Focus                                  |
| --- | ------------------------------------------------- | ------------------ | -------------------------------------- |
| 1   | _Artificial Intelligence: A Modern Approach_      | Russell & Norvig   | Definitive text on intelligent agents  |
| 2   | _The Alignment Problem_                           | Brian Christian    | How AI goals diverge from human values |
| 3   | _AI Agents: The Definitive Guide_                 | Nicole Koenigstein | Modern agent architectures             |
| 4   | _Human Compatible: AI and the Problem of Control_ | Stuart Russell     | AI autonomy and control                |

### 📹 Video Resources

| #   | Video                          | Link                                                                     |
| --- | ------------------------------ | ------------------------------------------------------------------------ |
| 1   | Agentic AI Overview (Stanford) | https://www.youtube.com/watch?v=kJLiOGle3Lw                              |
| 2   | Building Effective Agents      | https://www.youtube.com/watch?v=D7_ipDqhtwk                              |
| 3   | Building an Agent from Scratch | https://www.youtube.com/watch?v=xzXdLRUyjUg                              |
| 4   | Building and Evaluating Agents | https://www.youtube.com/watch?v=d5EltXhbcfA                              |
| 5   | Philo Agents Playlist          | https://www.youtube.com/playlist?list=PLacQJwuclt_sV-tfZmpT1Ov6jldHl30NR |

---

## Key Takeaways

```
┌─────────────────────────────────────────────────────────────────┐
│              WEEK 7 — KEY TAKEAWAYS                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  1. AUTONOMY IS A SPECTRUM, NOT A SWITCH                         │
│     From tools (Level 1) to fully autonomous agents (Level 5).   │
│     Choose the right level for your risk tolerance               │
│     and use case. Start low, graduate up.                        │
│                                                                  │
│  2. GOAL-DIRECTEDNESS IS CAPABILITY; ALIGNMENT IS SAFETY         │
│     A capable, goal-directed agent is dangerous if its goals     │
│     aren't aligned with human values. Both matter.               │
│                                                                  │
│  3. REACTIVE ≠ WORSE; DELIBERATIVE ≠ BETTER                     │
│     The best agents are HYBRIDS: reactive for immediate          │
│     responses, deliberative for complex planning.                │
│     Match the architecture to the task requirements.             │
│                                                                  │
│  4. PEAS IS YOUR DESIGN NORTH STAR                               │
│     Before building any agent, fully characterize its            │
│     environment using PEAS + six dimensions. The environment     │
│     dictates the agent architecture.                             │
│                                                                  │
│  5. PERCEIVED AGENCY IS A UX AND ETHICS CHALLENGE                │
│     Too little → users ignore the agent.                         │
│     Too much → users over-trust or feel deceived.                │
│     Calibrate perceived agency to actual capabilities.           │
│                                                                  │
│  6. DESIGN FROM THE ENVIRONMENT UP, NOT THE MODEL DOWN           │
│     Don't start with "I want to use GPT-4." Start with          │
│     "What environment does my agent operate in?" and let         │
│     that drive every design decision.                            │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## Study Checklist

### Foundation (Days 1-2)

- [ ] Read Russell & Norvig Chapter 2: Intelligent Agents
- [ ] Watch Stanford's "Agentic AI Overview" video
- [ ] Study the five levels of autonomy with examples
- [ ] Understand the PEAS framework and apply to 3 examples

### Deep Dive (Days 3-4)

- [ ] Compare reactive vs. deliberative architectures
- [ ] Classify environments for 5 different agent use cases
- [ ] Study goal-directedness and the goal hierarchy
- [ ] Explore perceived agency research and its implications

### Application (Days 5-6)

- [ ] Design a complete PEAS specification for your own agent project
- [ ] Create a layered hybrid architecture (reactive + deliberative)
- [ ] Define autonomy levels and escalation protocols for an agent
- [ ] Analyze perceived agency in 3 commercial AI products (Siri, ChatGPT, Devin)

### Synthesis (Day 7)

- [ ] Complete all study questions
- [ ] Write a design document for an agent using the Integrated Design Framework
- [ ] Compare two agents across all five core concepts
- [ ] Present your analysis to peers

---

_Last Updated: February 2026_
_Part of the AI Agents Comprehensive Study Guide Series_
_Compiled from academic texts, official industry guides, and AI research papers_
