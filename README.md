# 🤖 AI Agents Playgrounds - Case Studies

> A comprehensive collection of AI Agent case studies showcasing real-world applications of Agentic AI, RAG, Multi-Agent Systems, and LLM-powered automation across various industries.

---

## 📚 Overview

This repository contains **9 detailed case studies** demonstrating the practical implementation of AI agents in different domains. Each project includes comprehensive documentation, architecture diagrams, technology stack details, and implementation guidelines.

---

## 🗂️ Case Studies

### 📁 Projects Folder (Financial, Healthcare, Legal)

| Project                                                                               | Domain                   | Key Technologies                                     |
| ------------------------------------------------------------------------------------- | ------------------------ | ---------------------------------------------------- |
| [**Financial Report Q&A Bot**](./projects/financial-report-qa-bot/)                   | BFSI, Financial Analysis | RAG, Vector Databases, LLMs, Hugging Face            |
| [**Patient Support & Medical Info Agent**](./projects/patient-support-medical-agent/) | Healthcare               | LangChain, LangGraph, MCP, Agentic AI                |
| [**Legal Document Processing System**](./projects/legal-document-processing/)         | Legal                    | Multi-Agent Systems, LangSmith, Human Feedback Loops |

### 📁 Case-Studies Folder (Travel, Healthcare Ops, Software Dev, QA, Retail, HR)

| Project                                                                              | Domain                  | Key Technologies                               |
| ------------------------------------------------------------------------------------ | ----------------------- | ---------------------------------------------- |
| [**Travel Agent Application**](./case-studies/travel-agent-application/)             | Travel, Personalization | MCP, Context Management, Agentic AI            |
| [**Healthcare Startup Application**](./case-studies/healthcare-startup-application/) | Healthcare, Automation  | ReAct, LangGraph, Planning & Reasoning         |
| [**Automated Software Development**](./case-studies/automated-software-development/) | Software Development    | Multi-Agent Systems, Workflow Automation       |
| [**QA Customer Service Chatbot**](./case-studies/qa-customer-service-chatbot/)       | Customer Service, QA    | LangSmith, Human Feedback Loops, Testing       |
| [**Retail Order Query Chatbot**](./case-studies/retail-order-query-chatbot/)         | Retail, E-commerce      | Multi-Agent Systems, Context-Aware Interaction |
| [**HR Policy Query Bot**](./case-studies/hr-policy-query-bot/)                       | Human Resources         | RAG, Prompt Engineering, Vector Databases      |

---

## 🎯 Skills & Technologies Covered

### Core AI/ML Skills

| Skill                                    | Projects                                               |
| ---------------------------------------- | ------------------------------------------------------ |
| **Retrieval-Augmented Generation (RAG)** | Financial Q&A, HR Policy Bot                           |
| **Agentic AI**                           | Travel Agent, Healthcare Startup, Retail Chatbot       |
| **Multi-Agent Systems**                  | Legal Processing, Software Development, Retail Chatbot |
| **Large Language Models (LLMs)**         | All projects                                           |
| **Prompt Engineering**                   | HR Policy Bot, Financial Q&A                           |
| **Vector Databases**                     | Financial Q&A, HR Policy Bot, Patient Support          |

### Frameworks & Tools

| Framework                        | Projects                                                            |
| -------------------------------- | ------------------------------------------------------------------- |
| **LangChain**                    | Patient Support, Travel Agent, Healthcare Startup                   |
| **LangGraph**                    | Patient Support, Healthcare Startup, Legal Processing, Software Dev |
| **LangSmith**                    | Legal Processing, QA Chatbot                                        |
| **MCP (Model Context Protocol)** | Patient Support, Travel Agent                                       |
| **Hugging Face**                 | Financial Q&A, Patient Support                                      |

### Domain-Specific Skills

| Domain         | Key Skills                                     |
| -------------- | ---------------------------------------------- |
| **Healthcare** | FHIR integration, Medical NLP, Compliance      |
| **Finance**    | Financial document analysis, Entity extraction |
| **Legal**      | Document processing, Compliance verification   |
| **Retail**     | E-commerce integration, Context management     |
| **HR**         | Policy management, Employee services           |

---

## 📊 Project Comparison

| Feature        | Financial Q&A | Medical Agent | Legal Proc | Travel | Healthcare Ops | Software Dev | QA Chatbot | Retail | HR Bot |
| -------------- | :-----------: | :-----------: | :--------: | :----: | :------------: | :----------: | :--------: | :----: | :----: |
| RAG            |      ✅       |      🔄       |     🔄     |   ❌   |       ❌       |      ❌      |     ❌     |   🔄   |   ✅   |
| Multi-Agent    |      ❌       |      ✅       |     ✅     |   ✅   |       ✅       |      ✅      |     ❌     |   ✅   |   ❌   |
| LangGraph      |      🔄       |      ✅       |     ✅     |   ✅   |       ✅       |      ✅      |     ❌     |   ✅   |   ❌   |
| MCP            |      ❌       |      ✅       |     ❌     |   ✅   |       ❌       |      ❌      |     ❌     |   ❌   |   ❌   |
| LangSmith      |      ❌       |      ❌       |     ✅     |   ❌   |       ❌       |      ❌      |     ✅     |   ❌   |   ❌   |
| Human Feedback |      ❌       |      ❌       |     ✅     |   ❌   |       ❌       |      ❌      |     ✅     |   ❌   |   🔄   |
| ReAct          |      ❌       |      ❌       |     ❌     |   ❌   |       ✅       |      ❌      |     ❌     |   ❌   |   ❌   |

Legend: ✅ Primary Feature | 🔄 Secondary Feature | ❌ Not Applicable

---

## 🚀 Getting Started

### Prerequisites

All projects require:

- Python 3.11+
- Docker and Docker Compose
- API keys for LLM providers (OpenAI, Anthropic, etc.)

### Quick Start

```bash
# Clone the repository
git clone https://github.com/your-org/ai-agents-playgrounds.git
cd ai-agents-playgrounds/case-studies

# Choose a project (example: Financial Report Q&A Bot)
cd projects/financial-report-qa-bot

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Configure environment
cp .env.example .env
# Edit .env with your API keys

# Run the application
uvicorn src.main:app --reload --port 8000
```

---

## 📁 Repository Structure

```
case-studies/
├── README.md                              # This file
│
├── projects/                              # First batch of projects
│   ├── financial-report-qa-bot/           # RAG-based financial Q&A
│   │   └── README.md
│   ├── patient-support-medical-agent/     # Healthcare assistant with MCP
│   │   └── README.md
│   └── legal-document-processing/         # Multi-agent legal system
│       └── README.md
│
└── case-studies/                          # Second batch of projects
    ├── travel-agent-application/          # Travel planning with MCP
    │   └── README.md
    ├── healthcare-startup-application/    # ReAct for healthcare ops
    │   └── README.md
    ├── automated-software-development/    # Multi-agent development
    │   └── README.md
    ├── qa-customer-service-chatbot/       # QA with LangSmith
    │   └── README.md
    ├── retail-order-query-chatbot/        # Multi-agent retail
    │   └── README.md
    └── hr-policy-query-bot/               # RAG for HR policies
        └── README.md
```

---

## 📈 Implementation Roadmap

### Phase 1: Foundation (Week 1-2)

- [ ] Set up development environment
- [ ] Configure API keys and infrastructure
- [ ] Implement core RAG pipeline (Financial Q&A, HR Policy Bot)

### Phase 2: Single Agent (Week 3-4)

- [ ] Build basic chatbot interfaces
- [ ] Implement prompt engineering
- [ ] Add document processing

### Phase 3: Multi-Agent (Week 5-6)

- [ ] Implement LangGraph orchestration
- [ ] Build specialized agents
- [ ] Add agent communication

### Phase 4: Advanced Features (Week 7-8)

- [ ] Integrate MCP for external tools
- [ ] Add LangSmith monitoring
- [ ] Implement human feedback loops

### Phase 5: Production (Week 9-10)

- [ ] Deploy to cloud infrastructure
- [ ] Set up monitoring and alerting
- [ ] Performance optimization

---

## 🛠️ Technology Stack Overview

### LLM Providers

- **OpenAI GPT-4**: Primary LLM for generation and reasoning
- **Anthropic Claude**: Alternative for specific use cases
- **Hugging Face**: Open-source models and embeddings

### Vector Databases

- **Pinecone**: Managed vector database (production)
- **Qdrant**: Self-hosted alternative
- **Chroma**: Development and testing

### Frameworks

- **LangChain**: LLM orchestration
- **LangGraph**: Multi-agent workflows
- **FastAPI**: API development

### Infrastructure

- **Docker**: Containerization
- **Kubernetes**: Orchestration
- **Redis**: Caching and sessions
- **PostgreSQL**: Metadata storage

---

## 📖 Learning Path

### Beginner

1. Start with **HR Policy Query Bot** - Simple RAG implementation
2. Move to **Financial Report Q&A Bot** - More complex RAG

### Intermediate

3. Explore **Travel Agent Application** - MCP integration
4. Study **Healthcare Startup Application** - ReAct reasoning

### Advanced

5. Build **Legal Document Processing System** - Full multi-agent
6. Master **QA Customer Service Chatbot** - LangSmith + feedback loops

---

## 🤝 Contributing

We welcome contributions! See individual project READMEs for specific contribution guidelines.

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

---

## 📄 License

This project is licensed under the MIT License - see individual project LICENSE files for details.

---

## 📞 Contact

- **Repository Issues**: [Create an issue](https://github.com/your-org/ai-agents-playgrounds/issues)
- **Documentation**: See individual project READMEs

---

<p align="center">
  Made with ❤️ for the AI Community
</p>

<p align="center">
  <i>Building the future of AI agents, one case study at a time.</i>
</p>
