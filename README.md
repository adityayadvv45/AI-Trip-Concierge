# 🌴 AI Trip Concierge — Hotel Travel Companion

> A post-booking AI travel companion designed to help hotel guests plan, explore, and navigate their trip.

## 🌐 Live Demo

**[Launch AI Trip Concierge →](https://ai-trip-concierge-beta.vercel.app/)**

[![GitHub](https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge\&logo=github)](https://github.com/adityayadvv45/AI-Trip-Concierge)

---

## 📌 Overview

Most travel platforms focus heavily on the booking experience and provide limited assistance once the reservation is complete.

**AI Trip Concierge** extends the guest experience beyond booking by acting as a digital travel companion. It uses the guest's booking context, a curated local knowledge base, AI tool-calling, itinerary generation, and proactive alerts to provide personalized assistance throughout the trip.

The current prototype is designed around a hotel stay in **Goa, India**, with curated information about restaurants, activities, transportation, places, weather, and local experiences.

---

## ✨ Key Features

### 🏨 Personalized Guest Dashboard

* Displays hotel booking and trip information.
* Supports guest-name onboarding and personalization.
* Shows coastal weather information including temperature, humidity, high tide timing, and sunset.
* Provides quick-access concierge actions.

### 🗓️ Smart Itinerary Generator

* Generates customizable **1–5 day itineraries**.
* Creates morning, afternoon, and evening activities.
* Uses hotel/area context when planning activities.
* Includes travel distance and timing information.
* Covers curated Goa destinations and experiences such as:

  * Aguada Fort
  * Fontainhas Latin Quarter
  * Basilica of Bom Jesus
  * Mandovi Sunset Cruise
  * Thalassa Siolim
  * Pousada by the Beach
  * Gunpowder Assagao

### 🤖 Conversational AI Concierge

The application provides a conversational interface for hotel guests to ask questions and receive local recommendations.

The backend supports tool-based interactions for:

* `search_restaurants`
* `search_activities`
* `get_transport_tips`
* `get_place_details`
* `get_weather_and_tide_info`

Recommendations are grounded in a curated local knowledge base rather than relying entirely on open-ended model generation.

The application also includes a fallback mechanism for demonstration and offline scenarios when the external AI service is unavailable.

### 🔔 Proactive Travel Alerts

The alert system can simulate contextual notifications such as:

* 🌧️ Evening rain advisories
* 🔑 Hotel check-in and room-key reminders
* 🌅 Golden-hour recommendations
* 🌊 High-tide advisories

Alerts can also be surfaced directly inside the concierge experience.

### 🛵 Local Transport Guide

Provides practical information about transportation options in Goa, including:

* GoaMiles
* Scooter rentals
* Motorcycle pilots / bike taxis
* Mandovi river ferries

---

## 🏗️ Architecture

```text
AI-Trip-Concierge/
│
├── backend/
│   ├── app/
│   │   ├── __init__.py
│   │   ├── main.py
│   │   ├── agent.py
│   │   ├── tools.py
│   │   ├── itinerary.py
│   │   └── alerts.py
│   │
│   └── data/
│       └── goa.json
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Navbar.tsx
│   │   │   ├── TripOverview.tsx
│   │   │   ├── ItineraryView.tsx
│   │   │   ├── AIChat.tsx
│   │   │   ├── RecommendationsView.tsx
│   │   │   ├── AlertsHub.tsx
│   │   │   └── TransportModal.tsx
│   │   │
│   │   ├── services/
│   │   │   └── api.ts
│   │   │
│   │   ├── types.ts
│   │   ├── App.tsx
│   │   ├── main.tsx
│   │   └── index.css
│   │
│   ├── index.html
│   ├── package.json
│   └── vite.config.ts
│
├── demo_script.md
├── requirements.txt
├── .env.example
└── README.md
```

### Request Flow

```text
Guest
  │
  ▼
React + TypeScript Frontend
  │
  │ REST API
  ▼
FastAPI Backend
  │
  ├── AI Agent / Tool Calling
  │
  ├── Itinerary Engine
  │
  ├── Alert Engine
  │
  └── Local Knowledge Base
          │
          ▼
      Goa Dataset
```

---

## 🛠️ Tech Stack

### Frontend

* React
* TypeScript
* Vite
* CSS

### Backend

* Python
* FastAPI
* REST APIs

### AI

* Anthropic Claude API
* Tool Calling
* Local knowledge-base retrieval
* Fallback recommendation engine

### Data

* Curated Goa travel dataset
* Structured JSON knowledge base

### Deployment

* Vercel
* FastAPI backend

---

## 🚀 Getting Started

### Prerequisites

Make sure you have:

* Python 3.10+
* Node.js 18+
* npm

### 1. Clone the Repository

```bash
git clone https://github.com/adityayadvv45/AI-Trip-Concierge.git
cd AI-Trip-Concierge
```

### 2. Backend Setup

From the project root:

```bash
pip install -r requirements.txt
```

Create your environment file:

```bash
copy .env.example .env
```

Add the required API configuration to `.env`.

Start the FastAPI server:

```bash
python -m uvicorn backend.app.main:app --host 127.0.0.1 --port 8000 --reload
```

Backend:

```text
http://127.0.0.1:8000
```

### 3. Frontend Setup

Open another terminal:

```bash
cd frontend
npm install
npm run dev
```

Frontend:

```text
http://127.0.0.1:5173
```

---

## 🧪 Demo Flow

### 1. Dashboard

Open the application and review the hotel booking context, guest information, and weather details.

### 2. Generate an Itinerary

Select the desired trip duration and generate a personalized multi-day itinerary.

### 3. Try the AI Concierge

Example prompts:

```text
What's a good place for dinner tonight?

What should I visit tomorrow?

How can I get around Goa?

What can I do near Candolim?

What's the weather like this evening?
```

The concierge uses the available tools and local knowledge base to generate recommendations.

### 4. Test Proactive Alerts

Use the alert controls to simulate travel-related notifications and observe how they are surfaced in the concierge experience.

### 5. Explore Transport

Open the Transport Guide to view available transportation options and practical travel guidance.

---

## 🔌 Core Backend Modules

| Module         | Responsibility                        |
| -------------- | ------------------------------------- |
| `main.py`      | FastAPI application and API endpoints |
| `agent.py`     | AI agent and tool-calling workflow    |
| `tools.py`     | Local search and recommendation tools |
| `itinerary.py` | Multi-day itinerary generation        |
| `alerts.py`    | Proactive travel-alert simulation     |
| `goa.json`     | Curated local travel knowledge base   |

---

## 🎯 Project Goals

The project demonstrates how an AI-powered post-booking experience can:

* Maintain continuity after hotel booking.
* Personalize recommendations using trip context.
* Combine LLM reasoning with structured local data.
* Use tool-calling for grounded recommendations.
* Generate useful itineraries instead of generic suggestions.
* Proactively surface relevant information during a trip.

---

## 🔮 Future Improvements

* Integrate real hotel booking APIs.
* Add live maps and navigation.
* Connect to real-time restaurant and activity availability.
* Add user authentication and persistent guest profiles.
* Replace simulated alerts with scheduled background jobs.
* Add multilingual concierge support.
* Extend the knowledge base beyond Goa.
* Add real-time flight and transportation information.

---

## 👨‍💻 Author

**Aditya Yadav**
** Abhinav Sahu **
**Aditya Prajapati**

--- 

## 📄 License

This project is developed for educational, portfolio, and demonstration purposes.
