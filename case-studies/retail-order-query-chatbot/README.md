# 🛒 Retail Order Query Chatbot

> A multi-agent system that enables dynamic, context-aware interactions to assist customers with product queries and order tracking, improving the overall shopping experience.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Architecture](#architecture)
- [Multi-Agent System](#multi-agent-system)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Context-Aware Interactions](#context-aware-interactions)
- [Testing](#testing)
- [Deployment](#deployment)
- [Future Enhancements](#future-enhancements)

---

## 🎯 Overview

### Objective

Enable dynamic, context-aware interactions that assist customers with product queries and order tracking by developing a retail chatbot using a multi-agent system, improving the overall shopping experience.

### Domain

- **Retail**
- **Customer Service**
- **E-commerce**

### Problem Statement

E-commerce customers face friction in their shopping journey:

- Difficulty finding product information quickly
- Frustrating order tracking experiences
- Long wait times for customer support
- Lack of personalized recommendations
- Inconsistent support across channels
- Poor context retention in conversations

### Solution

A multi-agent retail chatbot that:

- Provides instant answers to product queries
- Offers real-time order tracking and updates
- Maintains context throughout the conversation
- Personalizes recommendations based on history
- Handles complex multi-step inquiries
- Integrates with e-commerce platforms seamlessly

---

## ✨ Key Features

| Feature                          | Description                                          |
| -------------------------------- | ---------------------------------------------------- |
| **Product Q&A**                  | Answer questions about products, availability, specs |
| **Order Tracking**               | Real-time order status and delivery updates          |
| **Personalized Recommendations** | AI-driven product suggestions                        |
| **Context Retention**            | Remember conversation context across sessions        |
| **Multi-Channel Support**        | Web, mobile, social media integration                |
| **Returns & Refunds**            | Handle return requests and refund inquiries          |
| **Inventory Checks**             | Real-time stock availability                         |
| **Cart Assistance**              | Help with cart management and checkout               |

### Agent Roles

| Agent                    | Responsibility                      |
| ------------------------ | ----------------------------------- |
| **Router Agent**         | Classify intent and route queries   |
| **Product Agent**        | Handle product-related queries      |
| **Order Agent**          | Manage order tracking and status    |
| **Recommendation Agent** | Provide personalized suggestions    |
| **Support Agent**        | Handle returns, refunds, complaints |
| **Checkout Agent**       | Assist with cart and checkout       |

---

## 🏗️ Architecture

### High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                    CUSTOMER TOUCHPOINTS                          │
│      (Website Chat / Mobile App / WhatsApp / Facebook)          │
└─────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                    OMNICHANNEL GATEWAY                           │
│              (Unified Message Handler)                          │
└─────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                RETAIL CHATBOT ORCHESTRATOR                       │
│                       (LangGraph)                               │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │                    Router Agent                           │  │
│  │           (Intent classification & routing)               │  │
│  └──────────────────────────────────────────────────────────┘  │
│                              │                                   │
│   ┌──────────┬──────────┬────┴────┬──────────┬──────────┐      │
│   ▼          ▼          ▼         ▼          ▼          ▼      │
│ ┌─────┐  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌────────┐ ┌────┐ │
│ │Prod │  │ Order   │ │ Recom   │ │ Support │ │Checkout│ │Cart│ │
│ │Agent│  │  Agent  │ │  Agent  │ │  Agent  │ │ Agent  │ │Agent│
│ └─────┘  └─────────┘ └─────────┘ └─────────┘ └────────┘ └────┘ │
└─────────────────────────────────────────────────────────────────┘
                                │
            ┌───────────────────┼───────────────────┐
            ▼                   ▼                   ▼
┌─────────────────┐   ┌─────────────────┐   ┌─────────────────┐
│    Product      │   │     Order       │   │    Customer     │
│    Catalog      │   │   Management    │   │    Profiles     │
│    (Vector DB)  │   │     System      │   │                 │
└─────────────────┘   └─────────────────┘   └─────────────────┘
```

### Conversation Flow

```
┌────────────┐    ┌────────────┐    ┌────────────┐    ┌────────────┐
│  Customer  │───▶│   Intent   │───▶│   Agent    │───▶│   Fetch    │
│  Message   │    │   Router   │    │  Selection │    │   Context  │
└────────────┘    └────────────┘    └────────────┘    └────────────┘
                                                            │
                       ┌────────────────────────────────────┘
                       │
                       ▼
┌────────────┐    ┌────────────┐    ┌────────────┐    ┌────────────┐
│   Update   │◀───│  Generate  │◀───│   Execute  │    │   Query    │
│  Context   │    │  Response  │    │   Actions  │◀───│  Backend   │
└────────────┘    └────────────┘    └────────────┘    └────────────┘
```

---

## 🤖 Multi-Agent System

### Agent Interaction Model

```
                    ┌─────────────────┐
                    │   Router Agent  │
                    │ (Intent & Route)│
                    └────────┬────────┘
                             │
          ┌──────────────────┼──────────────────┐
          │                  │                  │
          ▼                  ▼                  ▼
    ┌──────────┐      ┌──────────┐      ┌──────────┐
    │ Product  │      │  Order   │      │  Support │
    │  Agent   │      │  Agent   │      │  Agent   │
    └────┬─────┘      └────┬─────┘      └────┬─────┘
         │                 │                 │
         ▼                 ▼                 ▼
    ┌──────────┐      ┌──────────┐      ┌──────────┐
    │ Product  │      │  Order   │      │  Ticket  │
    │ Catalog  │      │  System  │      │  System  │
    └──────────┘      └──────────┘      └──────────┘
```

### Agent Descriptions

#### 1. Router Agent

- **Purpose**: Classify customer intent and route to appropriate agent
- **Intents**: product_query, order_status, recommendation, return_request, cart_help, general_inquiry
- **Tools**: Intent classifier, context analyzer

#### 2. Product Agent

- **Purpose**: Answer product-related questions
- **Capabilities**: Search products, compare items, check availability, provide specs
- **Tools**: Product search, inventory API, product knowledge base

#### 3. Order Agent

- **Purpose**: Handle order tracking and status inquiries
- **Capabilities**: Track orders, estimate delivery, provide shipping updates
- **Tools**: Order management API, shipping carrier APIs

#### 4. Recommendation Agent

- **Purpose**: Provide personalized product recommendations
- **Capabilities**: Suggest products, upsell, cross-sell, handle preferences
- **Tools**: Recommendation engine, customer profile, purchase history

#### 5. Support Agent

- **Purpose**: Handle returns, refunds, and complaints
- **Capabilities**: Process returns, initiate refunds, escalate issues
- **Tools**: Returns API, ticketing system, policy database

#### 6. Checkout Agent

- **Purpose**: Assist with cart and checkout
- **Capabilities**: Apply coupons, update cart, payment assistance
- **Tools**: Cart API, coupon system, payment gateway

---

## 🛠️ Technology Stack

### Core Technologies

| Category            | Technology            | Purpose                        |
| ------------------- | --------------------- | ------------------------------ |
| **Language**        | Python 3.11+          | Primary development language   |
| **Agent Framework** | LangGraph             | Multi-agent orchestration      |
| **LLM Framework**   | LangChain             | LLM integration                |
| **LLM Provider**    | OpenAI GPT-4 / Claude | Conversation and reasoning     |
| **Vector Database** | Pinecone / Qdrant     | Product search                 |
| **API Framework**   | FastAPI               | REST API implementation        |
| **Session Store**   | Redis                 | Context and session management |
| **Database**        | PostgreSQL            | Customer and order data        |

### E-commerce Integrations

| Category                | Technology                      | Purpose              |
| ----------------------- | ------------------------------- | -------------------- |
| **E-commerce Platform** | Shopify / Magento / WooCommerce | Store integration    |
| **Shipping**            | ShipStation / EasyPost          | Tracking integration |
| **Payments**            | Stripe / PayPal                 | Payment status       |
| **Messaging**           | Twilio / WhatsApp               | Channel integration  |

---

## 📁 Project Structure

```
06-retail-order-query-chatbot/
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
│   │   │   ├── products.py
│   │   │   ├── orders.py
│   │   │   └── webhooks.py
│   │   ├── middleware/
│   │   └── schemas/
│   │
│   ├── agents/
│   │   ├── __init__.py
│   │   ├── router_agent.py          # Intent routing
│   │   ├── product_agent.py         # Product queries
│   │   ├── order_agent.py           # Order tracking
│   │   ├── recommendation_agent.py  # Recommendations
│   │   ├── support_agent.py         # Returns/refunds
│   │   ├── checkout_agent.py        # Cart assistance
│   │   └── tools/
│   │       ├── product_search.py
│   │       ├── order_lookup.py
│   │       ├── inventory_check.py
│   │       ├── return_processor.py
│   │       └── coupon_validator.py
│   │
│   ├── context/
│   │   ├── __init__.py
│   │   ├── context_manager.py       # Conversation context
│   │   ├── customer_profile.py      # Customer data
│   │   ├── session_manager.py       # Session handling
│   │   └── history_tracker.py       # Conversation history
│   │
│   ├── product/
│   │   ├── __init__.py
│   │   ├── catalog.py               # Product catalog
│   │   ├── search_engine.py         # Product search
│   │   ├── inventory.py             # Stock management
│   │   └── embeddings.py            # Product embeddings
│   │
│   ├── order/
│   │   ├── __init__.py
│   │   ├── order_manager.py         # Order management
│   │   ├── tracking.py              # Shipment tracking
│   │   └── status_notifier.py       # Status updates
│   │
│   ├── recommendations/
│   │   ├── __init__.py
│   │   ├── engine.py                # Recommendation engine
│   │   ├── collaborative.py         # Collaborative filtering
│   │   └── content_based.py         # Content-based filtering
│   │
│   ├── integrations/
│   │   ├── __init__.py
│   │   ├── shopify_client.py        # Shopify integration
│   │   ├── shipping_client.py       # Shipping APIs
│   │   ├── whatsapp_client.py       # WhatsApp integration
│   │   └── facebook_client.py       # Messenger integration
│   │
│   ├── channels/
│   │   ├── __init__.py
│   │   ├── web_handler.py           # Web chat
│   │   ├── whatsapp_handler.py      # WhatsApp
│   │   ├── facebook_handler.py      # Messenger
│   │   └── sms_handler.py           # SMS
│   │
│   └── utils/
│       ├── formatters.py
│       └── validators.py
│
├── tests/
│   ├── unit/
│   ├── integration/
│   └── e2e/
│
├── data/
│   ├── product_catalog/
│   └── sample_orders/
│
├── notebooks/
│   ├── 01_product_embeddings.ipynb
│   └── 02_recommendation_engine.ipynb
│
└── config/
    ├── agents.yaml
    └── channels.yaml
```

---

## 🚀 Installation

### Prerequisites

- Python 3.11+
- Docker and Docker Compose
- API keys for LLM and e-commerce platforms

### Quick Start

```bash
# Clone repository
git clone https://github.com/your-org/retail-chatbot.git
cd retail-chatbot

# Create virtual environment
python -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Set up environment
cp .env.example .env

# Index product catalog
python scripts/index_products.py

# Run application
uvicorn src.main:app --reload --port 8000
```

---

## ⚙️ Configuration

### Environment Variables

```bash
# Application
APP_NAME=retail-chatbot
APP_ENV=development

# LLM
OPENAI_API_KEY=sk-your-key

# Vector Database
PINECONE_API_KEY=your-key
PINECONE_INDEX=products

# E-commerce
SHOPIFY_STORE_URL=your-store.myshopify.com
SHOPIFY_ACCESS_TOKEN=your-token

# Shipping
EASYPOST_API_KEY=your-key

# Channels
WHATSAPP_TOKEN=your-token
FACEBOOK_PAGE_ACCESS_TOKEN=your-token

# Database
DATABASE_URL=postgresql://user:pass@localhost/retail
REDIS_URL=redis://localhost:6379
```

---

## 📖 Usage

### Sample Conversations

**Product Query:**

```
Customer: "Do you have the iPhone 15 Pro in blue?"

Chatbot: "Yes! We have the iPhone 15 Pro in Blue Titanium available.
Here are your options:

📱 iPhone 15 Pro - Blue Titanium
• 128GB - $999 ✅ In Stock
• 256GB - $1,099 ✅ In Stock
• 512GB - $1,299 ⚠️ Low Stock (2 left)
• 1TB - $1,499 ✅ In Stock

Would you like more details on any of these, or shall I add one to your cart?"
```

**Order Tracking:**

```
Customer: "Where is my order?"

Chatbot: "I found your recent order! Here's the status:

📦 Order #12345
Status: In Transit 🚚

Shipped: Jan 3, 2024
Carrier: FedEx
Tracking: 7894561230123

📍 Latest Update (2 hours ago):
Package departed Memphis, TN - On the way to your city

📅 Estimated Delivery: Jan 5, 2024

Would you like me to send you updates when the package is out for delivery?"
```

### Python SDK

```python
from retail_chatbot import RetailChatbot

chatbot = RetailChatbot()

# Chat with context
session = chatbot.create_session(customer_id="CUST123")

response = session.chat("I'm looking for running shoes under $150")
print(response.message)
print(response.products)  # Product recommendations

response = session.chat("Do you have them in size 10?")
# Context retained - knows we're discussing running shoes
```

---

## 🔄 Context-Aware Interactions

### Context Management

```python
from retail_chatbot import ContextManager

context = ContextManager()

# Context includes:
context.customer = {
    "id": "CUST123",
    "name": "John Doe",
    "loyalty_tier": "Gold",
    "preferences": ["electronics", "running"],
    "recent_orders": ["ORD123", "ORD124"]
}

context.conversation = {
    "current_topic": "product_search",
    "product_focus": "running_shoes",
    "filters_applied": {"price_max": 150},
    "cart_items": []
}

context.history = [
    {"role": "user", "content": "I'm looking for running shoes"},
    {"role": "assistant", "content": "Here are some great options..."}
]
```

### Multi-Turn Context Flow

```
Turn 1: "Show me Nike running shoes"
        → Context: {product_type: "running_shoes", brand: "Nike"}

Turn 2: "In size 10"
        → Context: {product_type: "running_shoes", brand: "Nike", size: 10}

Turn 3: "Under $150"
        → Context: {product_type: "running_shoes", brand: "Nike", size: 10, max_price: 150}

Turn 4: "Add the first one to cart"
        → Context preserved, adds product to cart
```

---

## 🧪 Testing

```bash
# Run all tests
pytest

# Test agents
pytest tests/unit/test_agents/

# Test context management
pytest tests/unit/test_context/
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
| **Memory**  | 4 GB    | 16+ GB      |
| **Storage** | 20 GB   | 100+ GB     |

---

## 🔮 Future Enhancements

- [ ] Visual product search (image upload)
- [ ] Voice assistant integration
- [ ] Live agent handoff
- [ ] Augmented reality try-on
- [ ] Price drop alerts
- [ ] Wishlist management
- [ ] Social proof integration
- [ ] Multi-language support

---

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

---

<p align="center">Made with ❤️ for Retail Innovation</p>
