# 5-Day Gen AI Intensive Course with Google

Completed notebooks from two Google/Kaggle intensive courses, adapted for local development:

1. **[5-Day Gen AI Intensive Course](https://www.kaggle.com/learn-guide/5-day-genai)** - Foundational GenAI concepts
2. **[5-Day AI Agents Intensive Course](https://www.kaggle.com/learn-guide/5-day-agents)** - Building AI agents with ADK

All 16 codelabs + 1 bonus notebook have been run locally with outputs.

## Repository Structure

```
Day-1-Foundational-LLMs-and-Prompt-Engineering/   # Prompting, evaluation, structured output
Day-2-Embeddings-and-Vector-Stores/                # RAG, similarity, Keras classification
Day-3-Generative-AI-Agents/                        # Function calling, LangGraph
Day-4-Domain-Specific-LLMs/                        # Fine-tuning, Google Search grounding
Day-5-MLOps-for-GenAI/                             # Agent-starter-pack review
Bonus/                                             # Multimodal, streaming, Live API, caching

AI-Agents-Intensive/
  Day-1/    # ADK agents, Sequential/Parallel/Loop architectures
  Day-2/    # Tools, MCP integration, long-running operations
  Day-3/    # Sessions, memory, context compaction
  Day-4/    # Observability (LoggingPlugin), evaluation (adk eval)
  Day-5/    # A2A protocol, Vertex AI Agent Engine deployment
```

## Course 1: Gen AI Intensive

| Day | Topic | Notebooks |
|-----|-------|-----------|
| 1 | Foundational LLMs & Prompt Engineering | Prompting fundamentals, Evaluation & structured output |
| 2 | Embeddings & Vector Stores | RAG with ChromaDB, Text similarity, Keras classification |
| 3 | Generative AI Agents | Function calling (SQL chatbot), LangGraph (BaristaBot) |
| 4 | Domain-Specific LLMs | Fine-tuning Gemini, Google Search grounding |
| 5 | MLOps for GenAI | Agent-starter-pack review |
| Bonus | Extra API Features | Multimodal, streaming, Live API, image generation, context caching |

## Course 2: AI Agents Intensive

| Day | Topic | Notebooks |
|-----|-------|-----------|
| 1 | Agents & Architectures | First ADK agent with google_search, Multi-agent patterns |
| 2 | Tools & Interoperability | FunctionTool/AgentTool, MCP + long-running operations |
| 3 | Sessions & Memory | InMemory/Database sessions, Memory with auto-callbacks |
| 4 | Agent Quality | Observability with LoggingPlugin, Evaluation with adk eval CLI |
| 5 | Prototype to Production | A2A protocol (to_a2a + RemoteA2aAgent), Vertex AI deployment |

## Running Locally

These notebooks were originally designed for Kaggle. All have been adapted for local use:

### Prerequisites

- Python 3.12+
- A [Gemini API key](https://aistudio.google.com/app/api-keys)
- (Day 5b only) Google Cloud account with [Application Default Credentials](https://cloud.google.com/docs/authentication/application-default-credentials)

### Setup

```bash
# Create .env file in the repo root
echo "GOOGLE_API_KEY=your-key-here" > .env

# Install core dependencies
pip install google-genai python-dotenv

# For AI Agents course
pip install google-adk

# Additional extras as needed
pip install "google-adk[eval]"    # Day 4b evaluation
pip install "google-adk[a2a]"     # Day 5a A2A protocol
pip install aiosqlite              # Day 3a database sessions
```

### Adaptations from Kaggle

- **Authentication**: `kaggle_secrets` replaced with `python-dotenv` loading from `.env`
- **File downloads**: `!wget` / `!curl` replaced with `requests.get()`
- **ADK Web UI**: Kaggle proxy sections skipped; agents run programmatically
- **Model updates**: Deprecated models replaced (see below)

## Model Deprecations

Some models used in the original notebooks have been deprecated:

| Original | Replacement |
|----------|-------------|
| `gemini-1.5-flash-001` | `gemini-2.0-flash-001` |
| `gemini-1.5-flash-001-tuning` | No longer available |
| `gemini-2.0-flash-exp` (Live API) | `gemini-2.5-flash-native-audio-latest` |

## Acknowledgments

- Course content by Google / Kaggle
- Original Gen AI notebooks by [markishere](https://www.kaggle.com/markishere)
- Original AI Agents notebooks by [kaggle5daysofai](https://www.kaggle.com/kaggle5daysofai)
