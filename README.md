# Ontario Driving Coach

Local stack for an Ontario driving-practice coach. Postgres (with pgvector) stores data and embeddings. Ollama serves the chat and embedding models. Application code is not in this repo yet.

## Layout

| Path | Role |
| --- | --- |
| `docker-compose.yml` | Postgres and Ollama |
| `services/ai` | AI service (planned) |
| `web` | Next.js app (planned) |
| `prompts` | Prompt files |
| `evals` | Eval cases; reports go in `evals/reports/` and stay untracked |
| `docs` | Design notes and ADRs |

## Prerequisites

- Docker
- A copy of `.env` from the template:

```bash
cp .env.example .env
```

Defaults match `docker-compose.yml`: database `driving_coach`, user `postgres`, password `postgres`, port `5432`.

## Run

```bash
docker compose up -d
```

| Service | URL |
| --- | --- |
| Postgres | `localhost:5432` |
| Ollama | `http://localhost:11434` |

Pull the models named in `.env.example` (`CHAT_MODEL`, `EMBED_MODEL`) before calling Ollama:

```bash
docker compose exec ollama ollama pull qwen2.5:7b-instruct
docker compose exec ollama ollama pull nomic-embed-text
```

`EMBED_DIM` must match the embedding model (768 for `nomic-embed-text`).

Stop the stack with `docker compose down`. The `pgdata` and `ollama` volumes keep the database and downloaded models.
