Udacity _Omni Trainer_ project: play trainee customer-service agent at ACME Enterprise while multimodal moderation (text, image, video, audio) watches every message. Built with Gemini + Pydantic AI agents, a Gradio chat UI and LLM customer, FastAPI moderation APIs, and Arize Phoenix tracing.

Based on Udacity course materials; see [LICENSE.md](LICENSE.md).

**Setup with [uv](https://docs.astral.sh/uv/)** (recommended; uses the lockfile):

```bash
uv sync --dev
```

**Or with pip:**

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
```

Copy `env.example` to `.env` and set `GEMINI_API_KEY` plus a non-empty `USER_API_KEY` (any local value works). If you use Google AI Studio directly, clear `GOOGLE_GEMINI_BASE_URL`.

Start the chat app, API, and Phoenix together:

```bash
uv run multimodal-moderation
# or, with the venv activated: multimodal-moderation
```

Then open:

- Chat UI: http://localhost:7860/
- Moderation API docs: http://localhost:8000/docs
- Phoenix traces: http://localhost:6006/projects

In the chat, you’re the trainee agent; an LLM plays an angry customer with a broken ACME Power Widget Pro. Try a normal reply, then something rude or PII-heavy, and watch moderation flag it with a rationale. Upload a file from `evals/test_data/` to exercise the image/audio/video agents.

The repo includes unit tests and Gemini-backed evals under `tests/` and `evals/` if you want to poke at the wiring or scoring (`uv run pytest tests/ -vv`, or `pytest` with the venv active).
