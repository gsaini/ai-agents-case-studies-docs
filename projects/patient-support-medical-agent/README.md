# 🏥 Patient Support & Medical Info Agent

> An intelligent healthcare assistant that aids patients in understanding health records, sourcing information from trusted medical knowledge bases, and maintaining context over multiple interactions.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Architecture](#architecture)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [MCP Integration](#mcp-integration)
- [Safety & Compliance](#safety--compliance)
- [Testing](#testing)
- [Deployment](#deployment)
- [Future Enhancements](#future-enhancements)

---

## 🎯 Overview

### Objective

Develop a healthcare assistant that aids patients in understanding health records, sourcing information from trusted medical knowledge bases, and maintaining context over multiple interactions.

### Domain

- **Healthcare**
- **Medical Information Systems**
- **Patient Support**

### Problem Statement

Patients often struggle with:

- Understanding complex medical terminology in their health records
- Finding reliable, trustworthy medical information
- Remembering previous conversations with healthcare providers
- Navigating the healthcare system effectively
- Getting timely answers to health-related questions

### Solution

An Agentic AI-powered healthcare assistant that:

- Interprets and explains medical records in plain language
- Sources information from verified medical knowledge bases
- Maintains conversation context across multiple sessions
- Provides personalized health information guidance
- Connects with healthcare systems via MCP (Model Context Protocol)

---

## ✨ Key Features

| Feature                          | Description                                                      |
| -------------------------------- | ---------------------------------------------------------------- |
| **Health Record Interpretation** | Translate complex medical documents into understandable language |
| **Medical Knowledge Q&A**        | Answer health questions using trusted medical databases          |
| **Conversation Memory**          | Remember past interactions for contextual responses              |
| **Multi-turn Dialogue**          | Support complex, multi-step health inquiries                     |
| **Medication Information**       | Provide drug information, interactions, and side effects         |
| **Symptom Checker**              | Preliminary symptom assessment with appropriate disclaimers      |
| **Appointment Assistance**       | Help schedule and prepare for medical appointments               |
| **Health Education**             | Deliver personalized health education content                    |

### Safety Features

- **Medical Disclaimer System**: Clear warnings about limitations
- **Emergency Detection**: Identify and escalate urgent situations
- **Source Citation**: Always cite medical information sources
- **Human Escalation**: Route to healthcare professionals when needed

---

## 🏗️ Architecture

### High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                    PATIENT INTERFACE                             │
│              (Web App / Mobile App / Voice)                     │
└─────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                      MCP SERVER LAYER                            │
│            (Model Context Protocol Integration)                 │
└─────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                    AGENTIC AI LAYER                              │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │                   LangGraph Orchestrator                  │  │
│  └──────────────────────────────────────────────────────────┘  │
│          │              │              │              │         │
│  ┌───────┴───┐  ┌───────┴───┐  ┌───────┴───┐  ┌───────┴───┐   │
│  │  Intent   │  │ Knowledge │  │  Record   │  │  Safety   │   │
│  │ Classifier│  │ Retriever │  │ Analyzer  │  │  Monitor  │   │
│  └───────────┘  └───────────┘  └───────────┘  └───────────┘   │
└─────────────────────────────────────────────────────────────────┘
                                │
            ┌───────────────────┼───────────────────┐
            ▼                   ▼                   ▼
┌─────────────────┐   ┌─────────────────┐   ┌─────────────────┐
│    Medical      │   │    Patient      │   │   Conversation  │
│   Knowledge     │   │   Records       │   │    Memory       │
│    Bases        │   │   (EHR/FHIR)    │   │   (LangGraph)   │
└─────────────────┘   └─────────────────┘   └─────────────────┘
```

### Agent Workflow (LangGraph)

```
                        ┌─────────────┐
                        │   START     │
                        └──────┬──────┘
                               │
                               ▼
                    ┌──────────────────┐
                    │  Intent Analysis │
                    └────────┬─────────┘
                             │
         ┌───────────────────┼───────────────────┐
         │                   │                   │
         ▼                   ▼                   ▼
┌────────────────┐  ┌────────────────┐  ┌────────────────┐
│ Record Query   │  │ Medical Info   │  │ General Health │
│    Agent       │  │    Agent       │  │    Agent       │
└────────┬───────┘  └────────┬───────┘  └────────┬───────┘
         │                   │                   │
         └───────────────────┼───────────────────┘
                             │
                             ▼
                    ┌────────────────┐
                    │ Safety Check   │
                    └────────┬───────┘
                             │
                  ┌──────────┴──────────┐
                  │                     │
                  ▼                     ▼
          ┌───────────┐         ┌───────────┐
          │  RESPOND  │         │  ESCALATE │
          └───────────┘         │  (Human)  │
                                └───────────┘
```

---

## 🛠️ Technology Stack

### Core Technologies

| Category              | Technology                      | Purpose                      |
| --------------------- | ------------------------------- | ---------------------------- |
| **Language**          | Python 3.11+                    | Primary development language |
| **Agent Framework**   | LangGraph                       | Multi-agent orchestration    |
| **LLM Orchestration** | LangChain                       | LLM integration and chains   |
| **LLM Provider**      | OpenAI GPT-4 / Anthropic Claude | Text generation              |
| **Embedding Models**  | Hugging Face Transformers       | Medical text embeddings      |
| **Protocol**          | MCP (Model Context Protocol)    | External system integration  |
| **API Framework**     | FastAPI                         | REST API implementation      |
| **Memory Store**      | Redis / PostgreSQL              | Conversation persistence     |

### Medical Integrations

| Category             | Technology            | Purpose                           |
| -------------------- | --------------------- | --------------------------------- |
| **Health Records**   | FHIR R4               | Standardized health data exchange |
| **Drug Database**    | RxNorm / DrugBank API | Medication information            |
| **Medical Ontology** | SNOMED CT / ICD-10    | Medical terminology               |
| **Knowledge Base**   | PubMed / MedlinePlus  | Medical research and education    |

### Infrastructure

| Category             | Technology           |
| -------------------- | -------------------- |
| **Containerization** | Docker               |
| **Orchestration**    | Kubernetes           |
| **Monitoring**       | Prometheus + Grafana |
| **Logging**          | ELK Stack            |
| **CI/CD**            | GitHub Actions       |

---

## 📁 Project Structure

```
02-patient-support-medical-agent/
├── README.md
├── requirements.txt
├── pyproject.toml
├── Dockerfile
├── docker-compose.yml
├── .env.example
│
├── src/
│   ├── main.py
│   │
│   ├── api/
│   │   ├── routes/
│   │   │   ├── chat.py
│   │   │   ├── health_records.py
│   │   │   └── medications.py
│   │   ├── middleware/
│   │   │   └── auth.py
│   │   └── schemas/
│   │       ├── request.py
│   │       └── response.py
│   │
│   ├── agents/
│   │   ├── __init__.py
│   │   ├── orchestrator.py          # LangGraph main orchestrator
│   │   ├── intent_classifier.py     # Intent detection agent
│   │   ├── record_analyzer.py       # Health record interpretation
│   │   ├── knowledge_retriever.py   # Medical knowledge Q&A
│   │   ├── medication_agent.py      # Drug information agent
│   │   ├── symptom_checker.py       # Symptom assessment
│   │   └── safety_monitor.py        # Safety and escalation
│   │
│   ├── mcp/
│   │   ├── __init__.py
│   │   ├── server.py                # MCP server implementation
│   │   ├── tools/
│   │   │   ├── ehr_tool.py          # EHR access tool
│   │   │   ├── drug_lookup.py       # Drug database tool
│   │   │   ├── appointment_tool.py  # Scheduling tool
│   │   │   └── knowledge_tool.py    # Medical KB tool
│   │   └── resources/
│   │       ├── patient_context.py   # Patient information resource
│   │       └── medical_history.py   # History resource
│   │
│   ├── knowledge/
│   │   ├── __init__.py
│   │   ├── medical_kb.py            # Medical knowledge base
│   │   ├── drug_database.py         # Medication database
│   │   ├── symptom_database.py      # Symptom information
│   │   └── embeddings.py            # Medical embeddings
│   │
│   ├── memory/
│   │   ├── __init__.py
│   │   ├── conversation_memory.py   # Conversation history
│   │   ├── patient_context.py       # Patient profile memory
│   │   └── session_manager.py       # Session management
│   │
│   ├── integrations/
│   │   ├── __init__.py
│   │   ├── fhir_client.py           # FHIR API client
│   │   ├── pubmed_client.py         # PubMed integration
│   │   └── drug_api_client.py       # Drug database client
│   │
│   ├── safety/
│   │   ├── __init__.py
│   │   ├── disclaimer.py            # Medical disclaimers
│   │   ├── emergency_detector.py    # Emergency situation detection
│   │   ├── content_filter.py        # Harmful content filter
│   │   └── escalation.py            # Human escalation logic
│   │
│   ├── prompts/
│   │   ├── __init__.py
│   │   ├── system_prompts.py        # System prompt templates
│   │   ├── medical_prompts.py       # Medical-specific prompts
│   │   └── safety_prompts.py        # Safety-related prompts
│   │
│   └── utils/
│       ├── medical_nlp.py           # Medical NLP utilities
│       ├── terminology.py           # Medical term mapping
│       └── formatters.py            # Response formatting
│
├── tests/
│   ├── unit/
│   │   ├── test_agents/
│   │   ├── test_mcp/
│   │   └── test_safety/
│   ├── integration/
│   │   ├── test_langgraph_flow.py
│   │   └── test_mcp_integration.py
│   └── e2e/
│       └── test_patient_scenarios.py
│
├── data/
│   ├── medical_terms/
│   ├── drug_interactions/
│   └── symptom_mappings/
│
├── notebooks/
│   ├── 01_medical_embeddings.ipynb
│   ├── 02_langgraph_development.ipynb
│   └── 03_safety_testing.ipynb
│
├── scripts/
│   ├── setup_knowledge_base.py
│   ├── import_drug_database.py
│   └── test_mcp_connection.py
│
├── config/
│   ├── agents.yaml
│   ├── mcp_config.yaml
│   └── safety_rules.yaml
│
└── docs/
    ├── API.md
    ├── MCP_INTEGRATION.md
    ├── SAFETY_GUIDELINES.md
    └── COMPLIANCE.md
```

---

## 🚀 Installation

### Prerequisites

- Python 3.11+
- Docker and Docker Compose
- API keys for LLM providers
- FHIR server access (optional)

### Quick Start

```bash
# Clone repository
git clone https://github.com/your-org/patient-support-agent.git
cd patient-support-agent

# Create virtual environment
python -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Set up environment
cp .env.example .env
# Edit .env with your configuration

# Initialize knowledge base
python scripts/setup_knowledge_base.py

# Run application
uvicorn src.main:app --reload --port 8000
```

### Docker Installation

```bash
docker-compose up --build
```

---

## ⚙️ Configuration

### Environment Variables

```bash
# Application
APP_NAME=patient-support-agent
APP_ENV=development

# API Keys
OPENAI_API_KEY=sk-your-key
ANTHROPIC_API_KEY=sk-ant-your-key

# LangGraph
LANGGRAPH_CHECKPOINT_DB=postgresql://user:pass@localhost/langgraph

# MCP Configuration
MCP_SERVER_PORT=3000
MCP_AUTH_SECRET=your-secret

# Knowledge Base
VECTOR_DB_URL=http://localhost:6333
MEDICAL_KB_INDEX=medical-knowledge

# FHIR Integration
FHIR_SERVER_URL=https://fhir.example.com
FHIR_CLIENT_ID=your-client-id
FHIR_CLIENT_SECRET=your-secret

# Safety Settings
EMERGENCY_ESCALATION_ENABLED=true
HUMAN_REVIEW_THRESHOLD=0.7
```

### Agent Configuration (config/agents.yaml)

```yaml
orchestrator:
  model: gpt-4-turbo
  temperature: 0.3
  max_iterations: 10

agents:
  intent_classifier:
    model: gpt-3.5-turbo
    confidence_threshold: 0.8

  record_analyzer:
    model: gpt-4-turbo
    include_disclaimers: true

  knowledge_retriever:
    model: gpt-4-turbo
    top_k_results: 5
    sources:
      - pubmed
      - medlineplus
      - drugbank

  safety_monitor:
    emergency_keywords:
      - "chest pain"
      - "difficulty breathing"
      - "suicidal"
    escalation_threshold: 0.9
```

---

## 📖 Usage

### Chat API

```python
from patient_support import PatientAgent

agent = PatientAgent(patient_id="patient_123")

# Simple health question
response = agent.chat("What does my latest blood test show?")
print(response.message)
print(response.sources)

# Follow-up with context
response = agent.chat("Is my cholesterol level concerning?")
print(response.message)
```

### Sample Interactions

**Example 1: Record Interpretation**

```
Patient: "I received my lab results but don't understand the numbers.
          My HbA1c is 7.2%. Is that good?"

Agent: "Let me help you understand your HbA1c result.

Your HbA1c of 7.2% measures your average blood sugar over the past
2-3 months. Here's what this means:

📊 Reference Ranges:
- Normal: Below 5.7%
- Prediabetes: 5.7% to 6.4%
- Diabetes: 6.5% or higher

Your level of 7.2% indicates diabetes, though it's relatively close
to the target of 7% that many doctors recommend for diabetic patients.

⚠️ Important: Please discuss these results with your healthcare
provider for personalized guidance and treatment adjustments.

Would you like me to explain more about managing blood sugar levels?"
```

**Example 2: Medication Query**

```
Patient: "I was prescribed metformin. Can I take it with ibuprofen?"

Agent: "Important information about taking metformin with ibuprofen:

⚠️ Potential Interaction:
Taking ibuprofen with metformin may increase the risk of a rare but
serious condition called lactic acidosis, especially if you have
kidney problems.

Recommendations:
1. Consult your doctor or pharmacist before combining these medications
2. If approved, monitor for symptoms like muscle pain, weakness, or
   difficulty breathing
3. Consider acetaminophen as an alternative pain reliever (after
   consulting your doctor)

Source: DrugBank, FDA Drug Interactions Database

⚕️ Please speak with your healthcare provider for personalized advice."
```

---

## 🔌 MCP Integration

### MCP Server Setup

The agent exposes an MCP server for integration with other systems:

```typescript
// MCP Client Example
const client = new MCPClient({
  serverUrl: "http://localhost:3000/mcp",
  authToken: process.env.MCP_AUTH_TOKEN,
});

// List available tools
const tools = await client.listTools();
// Available: get_patient_records, lookup_drug, check_symptoms, etc.

// Use a tool
const result = await client.callTool("lookup_drug", {
  drug_name: "metformin",
  info_type: "interactions",
});
```

### Available MCP Tools

| Tool                   | Description                           |
| ---------------------- | ------------------------------------- |
| `get_patient_records`  | Retrieve patient health records       |
| `lookup_drug`          | Get drug information and interactions |
| `check_symptoms`       | Preliminary symptom assessment        |
| `schedule_appointment` | Book medical appointments             |
| `get_medical_info`     | Query medical knowledge base          |

### MCP Resources

| Resource                | Description              |
| ----------------------- | ------------------------ |
| `patient://context`     | Current patient profile  |
| `patient://history`     | Medical history summary  |
| `patient://medications` | Current medications list |

---

## 🛡️ Safety & Compliance

### Medical Safety Features

1. **Disclaimer Injection**: All medical responses include appropriate disclaimers
2. **Emergency Detection**: Automatic detection of emergency situations
3. **Source Citation**: All medical information includes sources
4. **Confidence Scoring**: Low-confidence responses trigger escalation
5. **Human Escalation**: Route complex cases to healthcare professionals

### Compliance Considerations

| Regulation         | Implementation                                    |
| ------------------ | ------------------------------------------------- |
| **HIPAA**          | PHI encryption, access controls, audit logging    |
| **GDPR**           | Data consent, right to deletion, data portability |
| **FDA Guidelines** | Clear disclaimers, no diagnostic claims           |

### Emergency Detection Keywords

```yaml
emergency_triggers:
  high_priority:
    - "chest pain"
    - "difficulty breathing"
    - "suicidal thoughts"
    - "severe bleeding"
  medium_priority:
    - "persistent fever"
    - "severe headache"
    - "allergic reaction"
```

---

## 🧪 Testing

```bash
# Run all tests
pytest

# With coverage
pytest --cov=src --cov-report=html

# Safety tests
pytest tests/unit/test_safety/

# LangGraph flow tests
pytest tests/integration/test_langgraph_flow.py
```

---

## 🚢 Deployment

### Production Requirements

| Component   | Minimum | Recommended |
| ----------- | ------- | ----------- |
| **CPU**     | 4 cores | 8+ cores    |
| **Memory**  | 8 GB    | 32+ GB      |
| **Storage** | 50 GB   | 200+ GB     |

### Kubernetes Deployment

```bash
kubectl apply -f k8s/
```

---

## 🔮 Future Enhancements

- [ ] Voice interface integration
- [ ] Multilingual support
- [ ] Wearable device data integration
- [ ] Predictive health alerts
- [ ] Telehealth video integration
- [ ] Family member proxy access
- [ ] Mental health specialized agent
- [ ] Integration with pharmacy systems

---

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

---

<p align="center">Made with ❤️ for Patient Care</p>
