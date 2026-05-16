# Agentic AI in a Nutshell

Hands-on Jupyter notebook for the Accenture internal knowledge-sharing session.  
Walks from a bare LLM call all the way to a stateful agent with persistent memory.

## What's inside

| Step | Topic |
|------|-------|
| 1 | Plain LLM call |
| 2 | Define tools — calculator + Tavily web search |
| 3 | LLM with tool calling |
| 4 | LangGraph agent workflow |
| 5 | Human-in-the-Loop approval |
| 6A | Without memory — agent forgets between calls |
| 6B | With memory — agent remembers across turns |
| Bonus | Full agent — tools + persistent memory |

## Prerequisites

- Python ≥ 3.10
- Gemini API key — [aistudio.google.com](https://aistudio.google.com/app/apikey) (free)
- Tavily API key — [app.tavily.com](https://app.tavily.com) (free tier)

## Setup

```bash
# 1. Create and activate the local venv
python3 -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

# 2. Install dependencies
pip install .

# 3. Register the venv as a Jupyter kernel (one-time)
python -m ipykernel install --user \
  --name langgraph-tutorial \
  --display-name "LangGraph Tutorial (.venv)"

# 4. Copy and fill in your API keys
cp .env.example .env
# edit .env with your GEMINI_API_KEY and TAVILY_API_KEY

# 5. Launch
jupyter lab agentic_ai_nutshell.ipynb
# select kernel → "LangGraph Tutorial (.venv)"
```

> Already set up? `source .venv/bin/activate` then open Jupyter.

## Environment variables

| Variable | Required | Description |
|----------|----------|-------------|
| `GEMINI_API_KEY` | Yes | Google Gemini model access |
| `TAVILY_API_KEY` | Yes | Web search tool |
| `LANGSMITH_API_KEY` | No | Trace runs in LangSmith UI |
| `LANGSMITH_TRACING` | No | Set `true` to enable tracing |

Copy `.env.example` → `.env`. The `.env` file is git-ignored.

## Stack

| | |
|-|-|
| Model | Gemini 2.5 Flash via `langchain-google-genai` |
| Orchestration | [LangGraph](https://langchain-ai.github.io/langgraph) |
| Search | [Tavily](https://docs.tavily.com) |
| Observability | [LangSmith](https://smith.langchain.com) (optional) |
| Dependencies | `pyproject.toml` — direct deps only |
