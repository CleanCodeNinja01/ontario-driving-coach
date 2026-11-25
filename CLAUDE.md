# Ontario Driving Coach

A local coach for Ontario driving practice. It answers from stored handbook material: Postgres with pgvector holds the text and embeddings, and Ollama runs the chat and embedding models. Nothing is sent to a hosted model unless `OPENAI_API_KEY` or `ANTHROPIC_API_KEY` is set.

Application code is not in this repo yet. Build the first service in `services/ai` before adding more services. The Next.js app belongs in `web`.

## Working in this repo

- Copy `.env.example` to `.env`. Never commit `.env`.
- Start Postgres and Ollama with `docker compose up -d`. Model names and `EMBED_DIM` live in `.env.example` (`qwen2.5:7b-instruct`, `nomic-embed-text`, 768).
- Keep prompts in `prompts/` and eval cases in `evals/`. `evals/reports/` is generated and gitignored.
- Design notes and ADRs go in `docs/`.
