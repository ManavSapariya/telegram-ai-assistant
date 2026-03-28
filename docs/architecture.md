# 🧠 System Architecture

## 📌 Overview

The **AI Telegram Personal Assistant** is designed using a **multi-agent workflow architecture** that integrates conversational AI with external tools and automation pipelines.

The system processes both **text and voice inputs**, interprets user intent, and executes actions such as scheduling events via Google Calendar.

---

## 🏗 High-Level Architecture

```plaintext
User (Telegram)
      ↓
Telegram Trigger
      ↓
Input Router (Switch Node)
   ├── Text Input
   └── Voice Input
          ↓
   Speech-to-Text (Whisper)
      ↓
AI Agent (Core Decision Engine)
      ↓
Tool Layer
   ├── Google Calendar API
   ├── Memory Module
   └── External Workflows
      ↓
Response Generator
      ↓
Telegram Output
```

---

## 🧩 Core Components

### 1. 📲 Telegram Interface

* Acts as the primary user interaction layer
* Supports both **text messages** and **voice recordings**
* Uses Telegram Bot API for communication

---

### 2. 🔀 Input Routing Layer

* Determines whether input is:

  * Text
  * Voice
* Routes accordingly to processing pipelines

---

### 3. 🎙 Speech Processing Module

* Converts voice messages into text
* Uses **Whisper API**
* Ensures multi-modal input capability

---

### 4. 🧠 AI Agent (Decision Engine)

The central component of the system.

#### Responsibilities:

* Understand user intent
* Decide which tool to use
* Generate appropriate responses
* Maintain conversation flow

#### Example Decisions:

| User Input                  | Action                |
| --------------------------- | --------------------- |
| "Schedule meeting tomorrow" | Call Calendar API     |
| "What is AI?"               | Generate response     |
| "What’s my schedule?"       | Fetch calendar events |

---

### 5. 🛠 Tool Layer

#### 📅 Google Calendar Integration

* Create events
* Update events
* Fetch events

#### 🧾 Memory Module

* Stores short-term context
* Helps maintain conversational continuity

#### 🔗 Workflow Integration

* Executes sub-flows (e.g., calendar workflows)

---

### 6. 🔄 Workflow Engine

* Built using tools like **n8n**
* Handles orchestration of:

  * Inputs
  * AI decisions
  * Tool execution
* Enables modular and scalable design

---

### 7. 📤 Response Layer

* Formats output
* Sends response back to Telegram user

---

## 🧠 Multi-Agent Perspective (Conceptual)

Although implemented as a single AI node, the system follows a **multi-agent logic**:

| Agent Type          | Role               |
| ------------------- | ------------------ |
| Planner Agent       | Understands intent |
| Executor Agent      | Calls tools        |
| Memory Agent        | Stores context     |
| Communication Agent | Responds to user   |

---

## 🔐 Security Considerations

* API keys stored in environment variables
* Secure webhook handling
* Controlled access to third-party services

---

## ⚙️ Scalability Design

The system is designed to scale with:

* Vector databases (for long-term memory)
* Microservices architecture
* Multi-user support
* Cloud deployment (Railway / Render)

---

## 📊 Architecture Goals

* Modular design
* Easy integration of new tools
* Multi-modal interaction
* Real-time response
* Extendable agent system

---

## 🧪 Current Limitations

* Basic memory (non-vector)
* Single-user focus
* Limited tool ecosystem

---

## 🚀 Future Direction

Refer to `future_scope.md` for upcoming improvements and production roadmap.
