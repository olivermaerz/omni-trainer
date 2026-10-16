Udacity *Omni Trainer* project: multimodal content moderation for ACME Enterprise customer-service training: text/image/video/audio agents (Gemini + Pydantic AI), a Gradio chat UI with an LLM customer, FastAPI moderation APIs, and Arize Phoenix tracing.

**Setup with [uv](https://docs.astral.sh/uv/)** (recommended; uses the lockfile):

```bash
uv sync --dev
```

**Or with pip:**

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
```

Copy `env.example` to `.env` and set `GEMINI_API_KEY` and a non-empty `USER_API_KEY` (any value works for local use). For Google AI Studio, remove or blank `GOOGLE_GEMINI_BASE_URL`.

Then start the chat app, API, and Phoenix together:

```bash
uv run multimodal-moderation
# or, with the venv activated: multimodal-moderation
```

- Chat UI: [http://localhost:7860/](http://localhost:7860/)
- Moderation API docs: [http://localhost:8000/docs](http://localhost:8000/docs)
- Phoenix traces: [http://localhost:6006/projects](http://localhost:6006/projects)

Run the unit tests with `uv run pytest tests/ -vv` (or `pytest tests/ -vv`). Evals live under `evals/` and call Gemini for real.