# AG2-Adaptive-Research-Team
A multi-agent AI research framework built on AG2, enabling adaptive team coordination, dynamic role assignment, and collaborative problem-solving across complex research tasks.

A Streamlit app that blends agent teamwork with agent-enabled routing and fallback, built entirely on AG2.

What This Shows
Agent teamwork: explicit roles and sequential handoffs
Agent-enabled routing: a clear decision step with local-doc vs web fallback
AG2-first implementation: no Microsoft AutoGen dependency; installs via ag2[openai]
Features
Local document upload (PDF, TXT, MD)
Routing decision based on document coverage
Optional web fallback via SearxNG
Verifier step to check evidence sufficiency
Final synthesis with citations
How To Run
Install dependencies:
pip install -r requirements.txt
Run the app:
streamlit run app.py
Provide your OpenAI API key in the sidebar and ask a question.
How It Works
Triage Agent decides whether the question should be answered from local docs or the web.
Local/Web Research Agent collects evidence.
Verifier Agent checks evidence strength.
Synthesizer Agent produces the final answer with citations.
Optional Add-ons (AG2 0.11)
AG-UI protocol integration for richer UI rendering
OpenTelemetry tracing for debugging multi-agent workflows
These are optional and not required to run this example.

Notes
Default model used is gpt-5-nano. You can change it in the sidebar before running a query.
Web fallback uses the SearxNG public instance at https://searxng.site/search. This instance may be rate-limited. # 🧠 AG2 Adaptive Research Team

> A multi-agent AI research framework built on AG2, enabling adaptive team coordination, dynamic role assignment, and collaborative problem-solving across complex research tasks.

---

## 📖 Overview

**AG2 Adaptive Research Team** is a multi-agent framework that simulates a fully collaborative AI research team. Built on top of [AG2 (AutoGen v2)](https://github.com/ag2ai/ag2), it dynamically assembles specialized agents — researchers, critics, planners, and synthesizers — that communicate, delegate, and adapt in real time to tackle complex, open-ended research problems.

Whether you're automating literature reviews, multi-step reasoning chains, or hypothesis generation, this framework provides the scaffolding to orchestrate intelligent agent teams with minimal setup.

---

## ✨ Features

- 🤝 **Adaptive Team Composition** — Agents are dynamically assigned roles based on the task at hand
- 🔄 **Multi-turn Collaboration** — Agents debate, refine, and synthesize outputs across multiple rounds
- 🧩 **Modular Agent Design** — Easily plug in custom agents or swap LLM backends
- 📚 **Research-Oriented Workflows** — Built-in support for literature search, summarization, fact-checking, and report generation
- 🛠️ **Tool Integration** — Agents can call external tools (web search, code execution, APIs)
- 📊 **Conversation Logging** — Full traceability of agent interactions and decisions
- ⚙️ **Config-Driven** — Define team structures and task pipelines via YAML/JSON

---

## 🏗️ Project Structure

```
ag2_adaptive_research_team/
│
├── agents/                  # Individual agent definitions
│   ├── planner.py           # High-level task decomposition agent
│   ├── researcher.py        # Literature & web research agent
│   ├── critic.py            # Evaluation and feedback agent
│   ├── synthesizer.py       # Report generation and summarization agent
│   └── coordinator.py       # Team orchestration and role assignment
│
├── teams/                   # Pre-built team configurations
│   ├── research_team.py     # Default research workflow
│   └── debate_team.py       # Adversarial critique workflow
│
├── tools/                   # External tool integrations
│   ├── web_search.py
│   ├── code_executor.py
│   └── document_loader.py
│
├── configs/                 # YAML configs for agents & pipelines
│   ├── agents.yaml
│   └── tasks.yaml
│
├── examples/                # Example use cases and notebooks
│   ├── basic_research.py
│   └── multi_round_debate.ipynb
│
├── tests/                   # Unit and integration tests
├── pyproject.toml
├── .gitignore
├── LICENSE
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.10+
- An OpenAI, Anthropic, or compatible LLM API key

### Installation

```bash
# Clone the repository
git clone https://github.com/<your-org>/AG2-Adaptive-Research-Team.git
cd AG2-Adaptive-Research-Team

# Create and activate a virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -e .
```

### Configuration

Set your API key as an environment variable:

```bash
export OPENAI_API_KEY="your-api-key-here"
```

Or create a `.env` file:

```env
OPENAI_API_KEY=your-api-key-here
```

---

## 🧪 Quick Example

```python
from ag2_adaptive_research_team.teams.research_team import ResearchTeam

team = ResearchTeam(
    topic="Recent advances in mixture-of-experts language models",
    rounds=3,
    output_format="report"
)

result = team.run()
print(result.summary)
```

The team will automatically:
1. **Plan** the research structure
2. **Search** for relevant information
3. **Critique** and cross-validate findings
4. **Synthesize** a final structured report

---

## 🤖 Agent Roles

| Agent | Role | Responsibilities |
|---|---|---|
| **Coordinator** | Orchestrator | Assigns tasks, manages turn-taking, resolves conflicts |
| **Planner** | Strategist | Breaks down complex tasks into subtasks |
| **Researcher** | Data Gatherer | Searches, retrieves, and summarizes information |
| **Critic** | Evaluator | Identifies gaps, biases, and logical errors |
| **Synthesizer** | Writer | Combines findings into coherent outputs |

---

## ⚙️ Configuration

Customize your team via `configs/agents.yaml`:

```yaml
team:
  name: adaptive_research_team
  max_rounds: 5
  consensus_threshold: 0.8

agents:
  - role: planner
    model: gpt-4o
    temperature: 0.3
  - role: researcher
    model: gpt-4o
    tools: [web_search, document_loader]
  - role: critic
    model: gpt-4o
    temperature: 0.2
  - role: synthesizer
    model: gpt-4o
    output_format: markdown
```

---

## 🧭 Roadmap

- [ ] Support for local LLMs (Ollama, LM Studio)
- [ ] Memory and context persistence across sessions
- [ ] Agent performance benchmarking suite
- [ ] Web UI for visualizing agent conversations
- [ ] RAG integration for private document corpora
- [ ] Human-in-the-loop interruption points

---

## 🤝 Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on submitting issues, feature requests, and pull requests.

```bash
# Run tests
pytest tests/

# Format code
ruff format .

# Lint
ruff check .
```

---

## 📄 License

This project is licensed under the **Apache License 2.0** — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [AG2 / AutoGen](https://github.com/ag2ai/ag2) — the underlying multi-agent conversation framework
- [Microsoft Research](https://www.microsoft.com/en-us/research/) — for foundational work on multi-agent systems
- The open-source AI community for continued inspiration

---

<p align="center">
  Built with 🤖 agents, ☕ caffeine, and a lot of inter-agent debate.
</p>
