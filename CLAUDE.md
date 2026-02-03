# 5-Day Gen AI Intensive Course with Google

## Project Overview
Self-paced learning project covering two Google/Kaggle courses:
1. **5-Day Gen AI Intensive Course** - https://www.kaggle.com/learn-guide/5-day-genai
2. **5-Day AI Agents Intensive Course** - https://www.kaggle.com/learn-guide/5-day-agents

Both courses fully completed. All 16 codelabs + 1 bonus notebook adapted for local use and executed.

## Repository Structure
```
FiveDayGenAIIntensiveCourseWithGoogle/
├── .env                          # GOOGLE_API_KEY (gitignored)
├── CLAUDE.md                     # This file
├── PROGRESS.md                   # Gen AI course progress tracker
├── Day-1-Prompting/              # Prompt engineering notebooks
├── Day-2-Embeddings/             # RAG, embeddings, Keras classification
├── Day-3-Agents/                 # Function calling, LangGraph
├── Day-4-Fine-Tuning/            # Fine-tuning, Google Search grounding
├── Day-5-MLOps/                  # Agent-starter-pack review
├── Bonus/                        # Multimodal, streaming, Live API, caching
└── AI-Agents-Intensive/          # Second course
    ├── PROGRESS.md               # AI Agents course progress tracker
    ├── Day-1/                    # ADK agents, architectures
    ├── Day-2/                    # Tools, MCP, long-running ops
    ├── Day-3/                    # Sessions, memory
    ├── Day-4/                    # Observability, evaluation
    └── Day-5/                    # A2A protocol, deployment
```

## Course 1: Gen AI Intensive - Completed
- **Day 1**: Foundational LLMs & Prompt Engineering (Gemini 2.0 API, prompt techniques, evaluation, structured output)
- **Day 2**: Embeddings & Vector Stores (RAG with ChromaDB, text similarity, Keras classification - 92% accuracy)
- **Day 3**: Generative AI Agents (function calling SQL chatbot, LangGraph BaristaBot agent)
- **Day 4**: Domain-Specific LLMs (fine-tuning baseline eval - tuning models deprecated, Google Search grounding)
- **Day 5**: MLOps for GenAI (agent-starter-pack review)
- **Bonus**: Multimodal (image/audio/video), streaming, Live API audio, image generation, context caching (322K tokens cached)

### Gen AI Notebook Adaptation Pattern
```python
import os
from dotenv import load_dotenv
load_dotenv(os.path.join(os.path.dirname(os.getcwd()), '.env'))
GOOGLE_API_KEY = os.getenv("GOOGLE_API_KEY")
```
- `kaggle_secrets` → `python-dotenv` loading from parent `.env`
- `!wget` / `!curl` → `requests.get()` with file write
- SDK: `google-genai` (1.7.0 for course, 1.9.0 for bonus)

## Course 2: AI Agents Intensive - Completed
- **Day 1**: From Prompt to Action (ADK agent + google_search), Agent Architectures (Sequential/Parallel/Loop agents, LLM orchestrator)
- **Day 2**: Agent Tools (FunctionTool, AgentTool, BuiltInCodeExecutor), Tools Best Practices (MCP via StdioConnectionParams, Long-Running Operations with human-in-the-loop)
- **Day 3**: Agent Sessions (InMemory/Database session services, context compaction, session state), Agent Memory (InMemoryMemoryService, load/preload memory, after_agent_callback auto-save)
- **Day 4**: Agent Observability (LoggingPlugin, custom CountInvocationPlugin, DEBUG logging, str vs List[str] bug demo), Agent Evaluation (adk eval CLI, evalset.json, test_config.json, response_match_score, tool_trajectory_avg_score)
- **Day 5**: A2A Communication (to_a2a(), RemoteA2aAgent, uvicorn server, product catalog e-commerce demo), Agent Deployment (deployed weather agent to Vertex AI Agent Engine europe-west4, tested live, cleaned up)

### AI Agents Notebook Adaptation Pattern
Uses grandparent .env path (notebooks are 2 levels deep):
```python
load_dotenv(os.path.join(os.path.dirname(os.path.dirname(os.getcwd())), '.env'))
```
- Model: `gemini-2.5-flash-lite` throughout
- Retry config: `HttpRetryOptions(attempts=5, exp_base=7, initial_delay=1, http_status_codes=[429, 500, 503, 504])`
- Kaggle proxy/web UI sections skipped; agents run programmatically via InMemoryRunner/Runner
- Extra installs: `aiosqlite` (for DatabaseSessionService), `google-adk[eval]`, `google-adk[a2a]`

## GCP Configuration
- Project: `aiagentsintensive`
- ADC credentials: `~/.config/gcloud/application_default_credentials.json`
- Used for Day 5b Vertex AI Agent Engine deployment
- No gcloud CLI installed; ADC file set up directly

## Model Deprecations Encountered
- `gemini-1.5-flash-001` → use `gemini-2.0-flash` or `gemini-2.0-flash-001`
- `gemini-1.5-flash-001-tuning` → no longer available via API
- `gemini-2.0-flash-exp` (Live API) → use `gemini-2.5-flash-native-audio-latest`
- `gemini-1.5-flash-001` (context caching) → use `gemini-2.0-flash-001`

## Environment Notes
- Platform: Linux (Ubuntu), Python 3.12
- API key stored in `.env` (gitignored), key: `GOOGLE_API_KEY`
- Kaggle API token: `KAGGLE_API_TOKEN` env var (for `~/.local/bin/kaggle` CLI)
- Kaggle notebooks downloaded from users `markishere` (Gen AI) and `kaggle5daysofai` (Agents)
- Keras uses JAX backend (`KERAS_BACKEND=jax`, no TensorFlow)
- Dependencies installed to ~/.local via `--user --break-system-packages`
- Kaggle web pages are JS-rendered; use kaggle CLI for notebook downloads
