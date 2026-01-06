# ✈️ Travel Agent Application

> An intelligent Agentic AI system that integrates tools and manages contexts to create personalized travel packages, boosting customer satisfaction and conversion rates.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Architecture](#architecture)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Configuration](#configuration)
- [MCP Integration](#mcp-integration)
- [Usage](#usage)
- [API Reference](#api-reference)
- [Testing](#testing)
- [Deployment](#deployment)
- [Future Enhancements](#future-enhancements)

---

## 🎯 Overview

### Objective

Utilize Agentic AI to integrate tools and manage contexts, enabling personalized travel packages that boost customer satisfaction and conversion rates.

### Domain

- **Travel**
- **Customer Experience**
- **Personalization**

### Problem Statement

Travel planning is complex and time-consuming:

- Customers struggle to find personalized travel options
- Manual coordination of flights, hotels, and activities is tedious
- Price comparison across multiple platforms is overwhelming
- Lack of real-time availability and pricing information
- Poor context retention across customer interactions
- Generic recommendations that don't match preferences

### Solution

An Agentic AI-powered travel assistant that:

- Understands customer preferences and travel history
- Integrates with multiple travel APIs via MCP
- Creates personalized, context-aware travel packages
- Provides real-time pricing and availability
- Manages complex multi-destination itineraries
- Maintains conversation context across interactions

---

## ✨ Key Features

| Feature                          | Description                                              |
| -------------------------------- | -------------------------------------------------------- |
| **Personalized Recommendations** | AI-driven suggestions based on preferences and history   |
| **Multi-Platform Integration**   | Connect to flights, hotels, car rentals, activities APIs |
| **Real-time Pricing**            | Live pricing and availability from multiple sources      |
| **Context Management**           | Remember customer preferences across sessions            |
| **Itinerary Building**           | Create comprehensive travel packages                     |
| **Price Comparison**             | Compare options across multiple providers                |
| **Booking Assistance**           | Guide users through the booking process                  |
| **Travel Alerts**                | Notify about price drops, schedule changes               |

### Agent Capabilities

| Agent              | Responsibility                                  |
| ------------------ | ----------------------------------------------- |
| **Planner Agent**  | Understand requirements and create travel plans |
| **Flight Agent**   | Search and compare flight options               |
| **Hotel Agent**    | Find and recommend accommodations               |
| **Activity Agent** | Suggest local experiences and tours             |
| **Budget Agent**   | Optimize packages within budget constraints     |
| **Booking Agent**  | Handle reservations and confirmations           |

---

## 🏗️ Architecture

### High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                     USER INTERFACES                              │
│           (Web App / Mobile App / Chat Widget)                  │
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
│                  TRAVEL AGENT ORCHESTRATOR                       │
│                       (LangGraph)                               │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │                  Supervisor Agent                         │  │
│  │           (Coordinates travel planning)                   │  │
│  └──────────────────────────────────────────────────────────┘  │
│                              │                                   │
│   ┌──────────┬──────────┬────┴────┬──────────┬──────────┐      │
│   ▼          ▼          ▼         ▼          ▼          ▼      │
│ ┌─────┐  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌────────┐ ┌────┐ │
│ │Plan │  │ Flight  │ │  Hotel  │ │Activity │ │ Budget │ │Book│ │
│ │Agent│  │  Agent  │ │  Agent  │ │  Agent  │ │ Agent  │ │Agent│
│ └─────┘  └─────────┘ └─────────┘ └─────────┘ └────────┘ └────┘ │
└─────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                      MCP SERVER LAYER                            │
│            (Model Context Protocol Integration)                 │
└─────────────────────────────────────────────────────────────────┘
                                │
        ┌───────────────────────┼───────────────────────┐
        ▼                       ▼                       ▼
┌───────────────┐       ┌───────────────┐       ┌───────────────┐
│   Flight APIs │       │  Hotel APIs   │       │ Activity APIs │
│ (Amadeus,     │       │ (Booking.com, │       │ (Viator,      │
│  Skyscanner)  │       │  Hotels.com)  │       │  GetYourGuide)│
└───────────────┘       └───────────────┘       └───────────────┘
```

### Conversation Flow

```
┌────────────┐    ┌────────────┐    ┌────────────┐    ┌────────────┐
│   User     │───▶│  Intent    │───▶│  Context   │───▶│  Agent     │
│  Message   │    │  Analysis  │    │  Retrieval │    │ Selection  │
└────────────┘    └────────────┘    └────────────┘    └────────────┘
                                                            │
    ┌───────────────────────────────────────────────────────┘
    │
    ▼
┌────────────┐    ┌────────────┐    ┌────────────┐    ┌────────────┐
│  Execute   │───▶│   Fetch    │───▶│  Generate  │───▶│   User     │
│   Tools    │    │   Results  │    │  Response  │    │  Response  │
└────────────┘    └────────────┘    └────────────┘    └────────────┘
```

---

## 🛠️ Technology Stack

### Core Technologies

| Category            | Technology                   | Purpose                        |
| ------------------- | ---------------------------- | ------------------------------ |
| **Language**        | Python 3.11+                 | Primary development language   |
| **Agent Framework** | LangGraph                    | Multi-agent orchestration      |
| **LLM Framework**   | LangChain                    | LLM integration                |
| **Protocol**        | MCP (Model Context Protocol) | External API integration       |
| **LLM Provider**    | OpenAI GPT-4 / Claude        | Conversation and reasoning     |
| **API Framework**   | FastAPI                      | REST API implementation        |
| **Context Storage** | Redis                        | Session and context management |
| **Database**        | PostgreSQL                   | User profiles and bookings     |

### Travel API Integrations

| Category        | APIs                                | Purpose                   |
| --------------- | ----------------------------------- | ------------------------- |
| **Flights**     | Amadeus, Skyscanner, Google Flights | Flight search and booking |
| **Hotels**      | Booking.com, Hotels.com, Expedia    | Accommodation search      |
| **Activities**  | Viator, GetYourGuide, TripAdvisor   | Tours and experiences     |
| **Car Rentals** | Hertz, Enterprise, Kayak            | Vehicle rentals           |
| **Weather**     | OpenWeatherMap                      | Destination weather info  |
| **Maps**        | Google Maps, Mapbox                 | Location and routing      |

---

## 📁 Project Structure

```
02-travel-agent-application/
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
│   │   │   ├── search.py
│   │   │   ├── bookings.py
│   │   │   └── preferences.py
│   │   ├── middleware/
│   │   └── schemas/
│   │
│   ├── agents/
│   │   ├── __init__.py
│   │   ├── supervisor.py           # LangGraph orchestrator
│   │   ├── planner_agent.py        # Trip planning
│   │   ├── flight_agent.py         # Flight search
│   │   ├── hotel_agent.py          # Hotel search
│   │   ├── activity_agent.py       # Activities and tours
│   │   ├── budget_agent.py         # Budget optimization
│   │   └── booking_agent.py        # Booking management
│   │
│   ├── mcp/
│   │   ├── __init__.py
│   │   ├── server.py               # MCP server
│   │   ├── tools/
│   │   │   ├── flight_search.py    # Flight API tool
│   │   │   ├── hotel_search.py     # Hotel API tool
│   │   │   ├── activity_search.py  # Activity API tool
│   │   │   ├── car_rental.py       # Car rental tool
│   │   │   ├── weather.py          # Weather API tool
│   │   │   └── maps.py             # Maps API tool
│   │   └── resources/
│   │       ├── user_preferences.py
│   │       └── trip_context.py
│   │
│   ├── context/
│   │   ├── __init__.py
│   │   ├── context_manager.py      # Context management
│   │   ├── user_profile.py         # User preferences
│   │   ├── trip_context.py         # Current trip context
│   │   └── history_manager.py      # Conversation history
│   │
│   ├── integrations/
│   │   ├── __init__.py
│   │   ├── amadeus_client.py       # Amadeus API
│   │   ├── booking_client.py       # Booking.com API
│   │   ├── viator_client.py        # Viator API
│   │   └── weather_client.py       # Weather API
│   │
│   ├── personalization/
│   │   ├── __init__.py
│   │   ├── recommender.py          # Recommendation engine
│   │   ├── preference_learner.py   # Learn from behavior
│   │   └── scoring.py              # Option scoring
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
│   ├── destinations/
│   └── sample_itineraries/
│
├── notebooks/
│   ├── 01_api_exploration.ipynb
│   └── 02_personalization.ipynb
│
└── config/
    ├── agents.yaml
    └── mcp_config.yaml
```

---

## 🚀 Installation

### Prerequisites

- Python 3.11+
- Docker and Docker Compose
- API keys for travel services (Amadeus, etc.)

### Quick Start

```bash
# Clone repository
git clone https://github.com/your-org/travel-agent-app.git
cd travel-agent-app

# Create virtual environment
python -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Set up environment
cp .env.example .env

# Run application
uvicorn src.main:app --reload --port 8000
```

---

## ⚙️ Configuration

### Environment Variables

```bash
# Application
APP_NAME=travel-agent
APP_ENV=development

# LLM
OPENAI_API_KEY=sk-your-key

# Travel APIs
AMADEUS_API_KEY=your-amadeus-key
AMADEUS_API_SECRET=your-amadeus-secret
BOOKING_API_KEY=your-booking-key
VIATOR_API_KEY=your-viator-key

# MCP
MCP_SERVER_PORT=3000

# Database
DATABASE_URL=postgresql://user:pass@localhost/travel
REDIS_URL=redis://localhost:6379
```

---

## 🔌 MCP Integration

### Available MCP Tools

| Tool                | Description                    |
| ------------------- | ------------------------------ |
| `search_flights`    | Search for flight options      |
| `search_hotels`     | Find accommodations            |
| `search_activities` | Discover tours and experiences |
| `get_weather`       | Get destination weather        |
| `create_itinerary`  | Build travel itinerary         |
| `book_service`      | Make a reservation             |

### MCP Resources

| Resource             | Description             |
| -------------------- | ----------------------- |
| `user://preferences` | User travel preferences |
| `trip://current`     | Current trip context    |
| `trip://history`     | Past trip history       |

---

## 📖 Usage

### Sample Conversation

```
User: "I want to plan a romantic getaway to Paris for next month"

Agent: "How wonderful! Paris is a beautiful destination for a romantic getaway!
Let me help you plan the perfect trip.

To create a personalized package, I'd like to know:
1. 📅 What are your preferred travel dates?
2. 💰 What's your approximate budget per person?
3. ⭐ Do you prefer boutique hotels or larger chains?
4. 🎭 Any specific experiences you're interested in?
   (Eiffel Tower, wine tasting, Louvre, etc.)

I'll search for the best flights, accommodations, and romantic activities
for you!"
```

### Python SDK

```python
from travel_agent import TravelAgent

agent = TravelAgent(user_id="user_123")

# Plan a trip
response = agent.chat(
    "Find me flights from NYC to Paris for Feb 14-21, under $1000"
)

print(response.flights)
print(response.recommendations)
```

---

## 🧪 Testing

```bash
pytest
pytest --cov=src --cov-report=html
```

---

## 🚢 Deployment

```bash
docker-compose up --build
```

---

## 🔮 Future Enhancements

- [ ] Voice interface integration
- [ ] Real-time price alerts
- [ ] Group travel coordination
- [ ] Loyalty program integration
- [ ] AR destination previews
- [ ] Multi-language support
- [ ] Visa requirements checker
- [ ] Travel insurance integration

---

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

---

<p align="center">Made with ❤️ for Travelers</p>
