# 📋 HR Policy Query Bot

> A RAG-powered HR policy query bot leveraging vector databases and prompt engineering to deliver accurate, efficient, and reliable employee query resolution.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Architecture](#architecture)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Configuration](#configuration)
- [RAG Implementation](#rag-implementation)
- [Prompt Engineering](#prompt-engineering)
- [Usage](#usage)
- [Testing](#testing)
- [Deployment](#deployment)
- [Future Enhancements](#future-enhancements)

---

## 🎯 Overview

### Objective

Build a RAG-powered HR policy query bot leveraging vector databases and prompt engineering to deliver accurate, efficient, and reliable employee query resolution.

### Domain

- **Human Resources**
- **Employee Services**
- **Knowledge Management**

### Problem Statement

HR departments face challenges in supporting employees:

- Employees struggle to find policy information quickly
- HR teams overwhelmed with repetitive queries
- Policy documents scattered across multiple systems
- Inconsistent answers to the same questions
- Long response times for simple inquiries
- Difficulty keeping employees informed of policy changes

### Solution

An intelligent HR policy bot that:

- Provides instant answers to policy questions
- Uses RAG to retrieve accurate information from policy documents
- Maintains source attribution for all responses
- Handles complex multi-document queries
- Ensures consistent and accurate responses
- Scales to support thousands of employees

---

## ✨ Key Features

| Feature                      | Description                                   |
| ---------------------------- | --------------------------------------------- |
| **Policy Q&A**               | Answer questions about company policies       |
| **Document Retrieval**       | Find relevant policy documents instantly      |
| **Source Citations**         | Cite specific sections and documents          |
| **Multi-Document Synthesis** | Answer questions spanning multiple policies   |
| **Personalized Responses**   | Context-aware based on employee role/location |
| **Policy Updates**           | Notify about recent policy changes            |
| **FAQ Generation**           | Identify common questions automatically       |
| **Escalation Handling**      | Route complex queries to HR team              |

### Supported Policy Categories

| Category             | Examples                                         |
| -------------------- | ------------------------------------------------ |
| **Leave & Time Off** | PTO, sick leave, holidays, parental leave        |
| **Benefits**         | Health insurance, 401k, wellness programs        |
| **Compensation**     | Salary reviews, bonuses, expense reimbursement   |
| **Workplace**        | Remote work, dress code, office policies         |
| **Conduct**          | Code of ethics, harassment, disciplinary actions |
| **Career**           | Performance reviews, promotions, training        |

---

## 🏗️ Architecture

### High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                    EMPLOYEE INTERFACES                           │
│         (Slack Bot / Teams Bot / Web Portal / Mobile)           │
└─────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                      API GATEWAY                                 │
│               (FastAPI + Authentication)                        │
└─────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                     HR POLICY BOT                                │
│                                                                  │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │                  RAG Pipeline                             │  │
│  │                                                           │  │
│  │  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐         │  │
│  │  │ Query  │──│Retrieve│──│ Rerank │──│Generate│         │  │
│  │  │ Process│  │ Chunks │  │ Results│  │Response│         │  │
│  │  └────────┘  └────────┘  └────────┘  └────────┘         │  │
│  └──────────────────────────────────────────────────────────┘  │
│                              │                                   │
│              ┌───────────────┼───────────────┐                  │
│              ▼               ▼               ▼                  │
│       ┌──────────┐    ┌──────────┐    ┌──────────┐             │
│       │ Context  │    │ Employee │    │ Response │             │
│       │ Builder  │    │  Profile │    │Formatter │             │
│       └──────────┘    └──────────┘    └──────────┘             │
└─────────────────────────────────────────────────────────────────┘
                                │
            ┌───────────────────┼───────────────────┐
            ▼                   ▼                   ▼
┌─────────────────┐   ┌─────────────────┐   ┌─────────────────┐
│    Vector       │   │    Policy       │   │    Employee     │
│    Database     │   │   Document      │   │    Database     │
│   (Qdrant)      │   │    Store        │   │   (PostgreSQL)  │
└─────────────────┘   └─────────────────┘   └─────────────────┘
```

### RAG Pipeline Flow

```
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│   Employee   │───▶│    Query     │───▶│   Semantic   │
│   Question   │    │  Processing  │    │    Search    │
└──────────────┘    └──────────────┘    └──────────────┘
                                              │
                                              ▼
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│   Deliver    │◀───│   Generate   │◀───│   Retrieve   │
│   Response   │    │   Answer     │    │   Chunks     │
└──────────────┘    └──────────────┘    └──────────────┘
```

### Document Ingestion Pipeline

```
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│   Policy     │───▶│   Extract    │───▶│   Chunk      │
│  Documents   │    │    Text      │    │    Text      │
│ (PDF/DOCX)   │    │              │    │              │
└──────────────┘    └──────────────┘    └──────────────┘
                                              │
                                              ▼
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│   Index      │◀───│   Create     │◀───│   Add        │
│   Ready      │    │  Embeddings  │    │  Metadata    │
└──────────────┘    └──────────────┘    └──────────────┘
```

---

## 🛠️ Technology Stack

### Core Technologies

| Category                | Technology                 | Purpose                      |
| ----------------------- | -------------------------- | ---------------------------- |
| **Language**            | Python 3.11+               | Primary development language |
| **RAG Framework**       | LangChain / LlamaIndex     | RAG pipeline                 |
| **Embedding Models**    | OpenAI / HuggingFace       | Text embeddings              |
| **Vector Database**     | Qdrant / Pinecone / Chroma | Vector storage               |
| **LLM Provider**        | OpenAI GPT-4 / Claude      | Response generation          |
| **API Framework**       | FastAPI                    | REST API                     |
| **Document Processing** | PyPDF2, python-docx        | Policy parsing               |
| **Database**            | PostgreSQL                 | Metadata storage             |

### Communication Integrations

| Category  | Technology      | Purpose               |
| --------- | --------------- | --------------------- |
| **Slack** | Slack Bolt      | Slack bot integration |
| **Teams** | Microsoft Graph | Teams bot integration |
| **Email** | SendGrid        | Email notifications   |

---

## 📁 Project Structure

```
07-hr-policy-query-bot/
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
│   │   │   ├── query.py
│   │   │   ├── documents.py
│   │   │   ├── feedback.py
│   │   │   └── admin.py
│   │   ├── middleware/
│   │   └── schemas/
│   │
│   ├── rag/
│   │   ├── __init__.py
│   │   ├── pipeline.py              # Main RAG pipeline
│   │   ├── query_processor.py       # Query enhancement
│   │   ├── retriever.py             # Document retrieval
│   │   ├── reranker.py              # Result reranking
│   │   ├── context_builder.py       # Context assembly
│   │   └── response_generator.py    # Answer generation
│   │
│   ├── document_processing/
│   │   ├── __init__.py
│   │   ├── loaders/
│   │   │   ├── pdf_loader.py
│   │   │   ├── docx_loader.py
│   │   │   └── confluence_loader.py
│   │   ├── chunkers/
│   │   │   ├── semantic_chunker.py
│   │   │   └── policy_chunker.py
│   │   └── metadata_extractor.py
│   │
│   ├── embeddings/
│   │   ├── __init__.py
│   │   ├── embedding_service.py
│   │   ├── models/
│   │   │   ├── openai_embeddings.py
│   │   │   └── hf_embeddings.py
│   │   └── caching.py
│   │
│   ├── vector_store/
│   │   ├── __init__.py
│   │   ├── qdrant_store.py
│   │   ├── pinecone_store.py
│   │   └── chroma_store.py
│   │
│   ├── prompts/
│   │   ├── __init__.py
│   │   ├── system_prompts.py
│   │   ├── hr_prompts.py
│   │   ├── templates/
│   │   │   ├── policy_qa.py
│   │   │   ├── benefits_qa.py
│   │   │   └── leave_qa.py
│   │   └── prompt_manager.py
│   │
│   ├── personalization/
│   │   ├── __init__.py
│   │   ├── employee_context.py
│   │   ├── location_policies.py
│   │   └── role_permissions.py
│   │
│   ├── integrations/
│   │   ├── __init__.py
│   │   ├── slack_bot.py
│   │   ├── teams_bot.py
│   │   └── hris_client.py
│   │
│   ├── analytics/
│   │   ├── __init__.py
│   │   ├── query_analytics.py
│   │   ├── faq_generator.py
│   │   └── usage_tracker.py
│   │
│   └── utils/
│       ├── formatters.py
│       └── validators.py
│
├── tests/
│   ├── unit/
│   │   ├── test_rag/
│   │   ├── test_embeddings/
│   │   └── test_prompts/
│   ├── integration/
│   └── e2e/
│
├── data/
│   ├── policies/
│   │   ├── leave_policy.pdf
│   │   ├── benefits_guide.pdf
│   │   └── employee_handbook.pdf
│   └── sample_queries/
│
├── notebooks/
│   ├── 01_document_processing.ipynb
│   ├── 02_embedding_experiments.ipynb
│   ├── 03_prompt_engineering.ipynb
│   └── 04_retrieval_tuning.ipynb
│
├── scripts/
│   ├── ingest_policies.py
│   ├── setup_vector_store.py
│   └── evaluate_retrieval.py
│
└── config/
    ├── rag_config.yaml
    ├── prompts.yaml
    └── policies_metadata.yaml
```

---

## 🚀 Installation

### Prerequisites

- Python 3.11+
- Docker and Docker Compose
- API keys for LLM and embedding providers

### Quick Start

```bash
# Clone repository
git clone https://github.com/your-org/hr-policy-bot.git
cd hr-policy-bot

# Create virtual environment
python -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Set up environment
cp .env.example .env

# Ingest policy documents
python scripts/ingest_policies.py

# Run application
uvicorn src.main:app --reload --port 8000
```

---

## ⚙️ Configuration

### Environment Variables

```bash
# Application
APP_NAME=hr-policy-bot
APP_ENV=development

# LLM
OPENAI_API_KEY=sk-your-key

# Vector Database
QDRANT_URL=http://localhost:6333
QDRANT_COLLECTION=hr-policies

# Embeddings
EMBEDDING_MODEL=text-embedding-ada-002

# Database
DATABASE_URL=postgresql://user:pass@localhost/hr_bot

# Integrations
SLACK_BOT_TOKEN=xoxb-your-token
SLACK_SIGNING_SECRET=your-secret
```

### RAG Configuration (config/rag_config.yaml)

```yaml
retrieval:
  top_k: 5
  min_score: 0.7
  reranking_enabled: true
  reranker_model: cross-encoder/ms-marco-MiniLM-L-6-v2

chunking:
  strategy: semantic
  chunk_size: 500
  chunk_overlap: 100
  preserve_sections: true

embedding:
  model: text-embedding-ada-002
  dimension: 1536
  batch_size: 100

generation:
  model: gpt-4-turbo
  temperature: 0.1
  max_tokens: 1000
  include_sources: true
```

---

## 🔍 RAG Implementation

### Document Ingestion

```python
from hr_bot import PolicyIngester

ingester = PolicyIngester()

# Ingest a policy document
result = ingester.ingest(
    file_path="data/policies/leave_policy.pdf",
    metadata={
        "category": "leave",
        "effective_date": "2024-01-01",
        "version": "2.0",
        "audience": ["all_employees"]
    }
)

print(f"Chunks created: {result.chunk_count}")
print(f"Embeddings stored: {result.embeddings_count}")
```

### Query Processing

```python
from hr_bot import PolicyQueryBot

bot = PolicyQueryBot()

# Simple query
response = bot.query(
    question="How many PTO days do I get per year?",
    employee_id="EMP123"  # For personalization
)

print(f"Answer: {response.answer}")
print(f"Sources: {response.sources}")
print(f"Confidence: {response.confidence}")
```

### Retrieval Pipeline

```python
from hr_bot.rag import RAGPipeline

pipeline = RAGPipeline()

# Step 1: Process query
processed_query = pipeline.process_query(
    "What's the policy for remote work?"
)

# Step 2: Retrieve relevant chunks
chunks = pipeline.retrieve(
    processed_query,
    top_k=5,
    filters={"category": ["workplace", "remote"]}
)

# Step 3: Rerank for relevance
ranked_chunks = pipeline.rerank(chunks, processed_query)

# Step 4: Generate response
response = pipeline.generate(
    query=processed_query,
    context=ranked_chunks
)
```

---

## ✍️ Prompt Engineering

### System Prompt Design

```python
SYSTEM_PROMPT = """You are an HR Policy Assistant for {company_name}.
Your role is to help employees find accurate information about company policies.

Guidelines:
1. Only answer based on the provided policy documents
2. Always cite the source document and section
3. If unsure, acknowledge uncertainty and suggest contacting HR
4. Be friendly, professional, and helpful
5. Consider the employee's role and location for personalized answers

Employee Context:
- Name: {employee_name}
- Department: {department}
- Location: {location}
- Employment Type: {employment_type}

Current Date: {current_date}
"""
```

### Category-Specific Prompts

```yaml
# config/prompts.yaml
prompts:
  leave_policy:
    template: |
      Based on the leave policy documents, answer the following question.
      Consider the employee's tenure ({tenure_years} years) when calculating 
      leave entitlements.

      Question: {question}

      Context from policies:
      {context}

      Provide a clear answer with specific numbers if applicable.
      Cite the relevant policy section.

  benefits:
    template: |
      Answer the benefits-related question using the provided documents.
      Consider the employee's enrollment status and plan type.

      Question: {question}

      Context from policies:
      {context}

      Include relevant deadlines or enrollment periods if applicable.
```

### Response Formatting

```python
RESPONSE_FORMAT_PROMPT = """
Format your response as follows:

📋 **Answer**
[Clear, concise answer to the question]

📄 **Source**
[Document name], [Section/Page reference]

💡 **Additional Info** (if relevant)
[Any helpful related information]

⚠️ **Note** (if applicable)
[Important caveats or exceptions]
"""
```

---

## 📖 Usage

### Sample Interactions

**Leave Query:**

```
Employee: "How many sick days do I have left?"

HR Bot: "📋 **Answer**
Based on our records and the Leave Policy (v2024.1), here's your sick leave status:

• Annual Entitlement: 10 days
• Used This Year: 3 days
• Remaining: 7 days

📄 **Source**
Leave & Time Off Policy, Section 3.2 - Sick Leave Entitlement

💡 **Additional Info**
Unused sick days do not roll over to the next year. The policy year resets on January 1st.

Would you like information on how to submit a sick leave request?"
```

**Benefits Query:**

```
Employee: "When is open enrollment?"

HR Bot: "📋 **Answer**
The 2024 Benefits Open Enrollment period is:

📅 **November 1 - November 15, 2024**

During this time, you can:
• Enroll in or change your health insurance plan
• Update your 401(k) contributions
• Add or remove dependents
• Enroll in optional benefits (dental, vision, life insurance)

📄 **Source**
Employee Benefits Guide 2024, Section 2.1 - Enrollment Periods

⚠️ **Note**
Changes made during open enrollment take effect on January 1, 2025.
If you miss the deadline, you can only make changes during a
qualifying life event.

Would you like me to explain any specific benefits in detail?"
```

### Slack Integration

```python
from slack_bolt import App
from hr_bot import PolicyQueryBot

app = App(token=SLACK_BOT_TOKEN)
bot = PolicyQueryBot()

@app.message("hr policy")
def handle_policy_query(message, say, client):
    # Get employee info from Slack
    user_info = client.users_info(user=message["user"])

    # Query the policy bot
    response = bot.query(
        question=message["text"],
        employee_email=user_info["user"]["profile"]["email"]
    )

    # Send response
    say(
        text=response.answer,
        blocks=[
            {"type": "section", "text": {"type": "mrkdwn", "text": response.answer}},
            {"type": "context", "elements": [
                {"type": "mrkdwn", "text": f"📄 Source: {response.sources[0]}"}
            ]}
        ]
    )
```

---

## 🧪 Testing

```bash
# Run all tests
pytest

# Test RAG pipeline
pytest tests/unit/test_rag/

# Test prompt templates
pytest tests/unit/test_prompts/

# Evaluate retrieval quality
python scripts/evaluate_retrieval.py
```

### Retrieval Evaluation

```python
from hr_bot.evaluation import RetrievalEvaluator

evaluator = RetrievalEvaluator()

# Run evaluation on test set
results = evaluator.evaluate(
    test_set_path="data/sample_queries/test_queries.json",
    metrics=["recall@5", "mrr", "ndcg"]
)

print(f"Recall@5: {results.recall_at_5}")
print(f"MRR: {results.mrr}")
print(f"NDCG: {results.ndcg}")
```

---

## 🚢 Deployment

```bash
docker-compose up --build
```

### Infrastructure Requirements

| Component   | Minimum | Recommended |
| ----------- | ------- | ----------- |
| **CPU**     | 2 cores | 4+ cores    |
| **Memory**  | 4 GB    | 8+ GB       |
| **Storage** | 10 GB   | 50+ GB      |

---

## 🔮 Future Enhancements

- [ ] Multi-language support
- [ ] Voice query interface
- [ ] Policy change notifications
- [ ] Interactive policy explorer
- [ ] HR Manager dashboard
- [ ] Automated FAQ generation
- [ ] Policy comparison tool
- [ ] Integration with HRIS systems

---

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

---

<p align="center">Made with ❤️ for HR Teams</p>
