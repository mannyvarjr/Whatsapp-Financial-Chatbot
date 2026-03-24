#  Multimodal WhatsApp Financial AI Agent (n8n + Redis + GPT-4o)

###  Project Overview
This project is a production-ready **WhatsApp AI Agent** specialized in financial assistance. Unlike basic chatbots, this system is **multimodal**, meaning it can "hear" voice notes, "see" images of financial documents, and "read" text to provide context-aware advice in a single conversation.

###  How It Works
* **Multimodal Routing**: A **Switch Node** identifies the incoming message type and triggers specific sub-flows:
    * **Audio**: Fetches the WhatsApp media, then uses **OpenAI Whisper** to transcribe the voice note into text.
    * **Images**: Downloads the media and uses **GPT-4o Vision** to analyze receipts, charts, or financial statements.
    * **Text**: Processes standard natural language queries.
* **Intelligent Debouncing (Redis)**: To prevent the AI from responding to every single message in a "burst" (e.g., when a user sends three messages in ten seconds), I implemented a **Redis-backed queue**. The system waits, collects all inputs, and then generates one comprehensive response.
* **Agentic Orchestration**: A **LangChain Agent** synthesizes all processed data (text + transcription + image analysis) to provide a grounded, professional financial response.
* **Memory Management**: Uses a **Buffer Window** to maintain context, ensuring the AI remembers previous parts of the financial discussion.

###  Key Technical Features
* **Advanced Flow Control**: Expert use of **Redis** for state management and message grouping to handle real-world user behavior.
* **Speech-to-Text & Computer Vision**: Integration of multimodal models to lower the friction for the end user.
* **API Management**: Complex orchestration of the **WhatsApp Business API** (Cloud API) for secure media handling.
* **Data Cleaning**: Uses **Set Nodes** and expressions to normalize data from different inputs before feeding it to the AI.

###  Tech Stack
* **Automation Platform**: n8n
* **AI Models**: GPT-4o (Vision), GPT-4o-mini, OpenAI Whisper
* **Databases**: Redis (Queue Management)
* **Messaging**: WhatsApp Business API
* **Core Skills**: Multimodal AI Integration, State Management, API Orchestration, Financial Prompt Engineering.
