# Chatbot Agent with Memory & Human-in-the-Loop

A simple chatbot agent built with Langgraph and LangChain.

## Features
- **Persistent memory** via `MemorySaver`
- **Human-in-the-loop** clarification using `interrupt` + `ask_user_for_clarification` tool
- **External search** integration (TavilySearch)
- Runs locally in VSCode **and** in LangGraph Studio UI

---

## 📁 Project Structure

```
Chatbot_Agent/
├── .dockerignore
├── .gitignore
├── README.md
├── .env                 # Your API keys 
├── langgraph.json       # Langgraph config which specifies the dependencies, graphs, environment variables
├── venv/                # Python virtual environment
├── .langgraph_api/      # LangGraph Studio cache (auto-created by langgraph dev command)
└── agent/
    ├── __init__.py
    ├── agent.py         # Graph definition & runtime
    └── utils/
        ├── __init__.py
        ├── nodes.py     # ToolNode wiring
        ├── state.py     # State schema
        └── tools.py     # tools
```

---

## 🛠️ Prerequisites

- Python 3.10+
- langchain
- langchain-tavily
- langchain-core
- langchain-community
- langchain-google-genai
- langgraph
- langgraph-cli[inmem]
- ipython
- python-dotenv

---

## 🔍 How It Works

- **Memory**  
  Uses `MemorySaver` to persist conversation history across sessions.

- **Human-in-the-Loop**  
  If the AI needs more detail, it triggers an `interrupt` and calls `ask_user_for_clarification`, pausing until you reply.

- **Tools**  
  - **TavilySearch**: external web/search queries  
  - **ask_user_for_clarification**: targeted follow-up questions  

---

## 🚀 How to Run Locally

### 1️⃣ Clone the repository
```bash
git clone https://github.com/yourusername/chatbot-agent.git
cd chatbot-agent
```

### 2️⃣ Create and activate a virtual environment
```bash
python -m venv venv
# On Windows
venv\Scripts\activate
# On Mac/Linux
source venv/bin/activate
```

### 3️⃣ Install dependencies
Since this project uses **LangGraph** with dependencies defined in `langgraph.json`, you do not need a `requirements.txt` file.
- install dependencies as listed inside `langgraph.json`.

### 4️⃣ Set up environment variables
Create a `.env` file in the root folder and add your API keys:
```bash
GOOGLE_API_KEY=your_google_api_key
TAVILY_API_KEY=your_tavily_api_key
LANGSMITH_API_KEY=your_langsmith_api_key
```

### 5️⃣ Prepare the code for local run
- **Uncomment** the `while True` interactive loop in `agent.py`.
- **Uncomment** the import of `dotenv` and `load_dotenv()` in both `agent.py` and `tools.py`.

### 6️⃣ Run the chatbot agent
```bash
python agent/agent.py
```

This will start the chatbot in an interactive terminal session.

---

## 🌐 Running in LangGraph Studio
- Follow steps: https://langchain-ai.lang.chat/langgraph/tutorials/langgraph-platform/local-server/
- (for run in langgraph studio docker is required)
---



