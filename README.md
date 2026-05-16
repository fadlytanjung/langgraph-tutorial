# Agentic AI in a Nutshell

Hands-on Jupyter notebook for the Accenture internal knowledge-sharing session.  
Walks from a bare LLM call all the way to a stateful agent with persistent memory.

## What you'll build

| Step | Topic |
|------|-------|
| 1 | Plain LLM call |
| 2 | Define tools (calculator + web search) |
| 3 | LLM with tool calling |
| 4 | LangGraph agent workflow |
| 5 | Human-in-the-Loop approval |
| 6 | Memory — with vs without |
| Bonus | Full agent (tools + memory combined) |

## Prerequisites

- Python ≥ 3.10
- A Gemini API key (free at [aistudio.google.com](https://aistudio.google.com/app/apikey))
- A Tavily API key (free tier at [app.tavily.com](https://app.tavily.com))

## Quick start

```bash
# 1. Clone / enter the repo
cd langgraph-tutorial

# 2. Create and activate the local virtual environment
python3 -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Register the venv as a Jupyter kernel (one-time)
python -m ipykernel install --user --name langgraph-tutorial \
       --display-name "LangGraph Tutorial (.venv)"

# 5. Set up your API keys
cp .env.example .env
# then edit .env and fill in your keys

# 6. Open the notebook
jupyter lab agentic_ai_nutshell.ipynb
# → select kernel "LangGraph Tutorial (.venv)"
```

> **Already set up?** Just `source .venv/bin/activate` before opening Jupyter.

## Environment variables

| Variable | Required | Description |
|----------|----------|-------------|
| `GEMINI_API_KEY` | Yes | Google Gemini model access |
| `TAVILY_API_KEY` | Yes | Web search tool |
| `LANGSMITH_API_KEY` | No | Trace runs in LangSmith UI |
| `LANGSMITH_TRACING` | No | Set to `true` to enable tracing |

Copy `.env.example` → `.env` and fill in your values. The `.env` file is git-ignored.

## Model

Uses **Gemini 2.5 Flash** (`gemini-2.5-flash`) via `langchain-google-genai`.

## Tech stack

- [LangGraph](https://langchain-ai.github.io/langgraph) — agent orchestration
- [LangChain Google GenAI](https://python.langchain.com/docs/integrations/chat/google_generative_ai/) — Gemini model
- [Tavily](https://docs.tavily.com) — web search
- [LangSmith](https://smith.langchain.com) — observability (optional)
