# cc-brain

**cc-brain** is a personal knowledge base and career intelligence repository for Collins Chidera Eze (`chideracollins`). It is the Git-backed content source that feeds **GBrain**, a personal brain / retrieval-augmented knowledge system. GBrain syncs this repository, embeds its pages into a searchable vector index (using a local Ollama embedding model), and lets the contents be queried semantically.

This repository is where notes, career evidence, projects, and GitHub activity live as plain Markdown files. It is human-readable, versioned with Git, and automatically synchronized and indexed by the GBrain autopilot daemon.

---

## What's inside

| Path | Purpose |
|------|---------|
| `README.md` | This overview of what cc-brain is and how to work with it. |
| `AGENTS.md` | Agent-facing instructions for AI tools and future sessions. |
| `career-dossier/` | Career evidence: resume, research, career record, repository inventory. |
| `github/` | Activity captured by the GitHub tracking bot (per-day + weekly rollup). |
| `.gbrain-bot/` | State/checkpoint for the GitHub bot (**not** indexed as knowledge). |

---

## How it works with GBrain

1. **Source registration** — this repo is registered with GBrain as the `my-repo` source:
   ```bash
   gbrain sources add cc-brain --path $(pwd) --force
   ```
2. **Sync** — GBrain imports the Markdown pages:
   ```bash
   gbrain sync --source cc-brain --all
   ```
3. **Embed** — pages are embedded into a vector index using a local Ollama model (`nomic-embed-text`, 768-dim) — no API key required:
   ```bash
   gbrain embed --all
   ```
4. **Autopilot** — a launchd service (`com.gbrain.autopilot`) runs on a schedule and keeps cc-brain synced and embedded automatically.

Because embeddings use **local Ollama**, the indexing pipeline works fully offline and without any paid API key.

---

## Syncing with GitHub

The repository is managed with Git and synchronized with a remote GitHub repo.

### One-time remote setup (if not already done)
```bash
gh repo create cc-brain --public --source=. --remote=origin
```

### Push local changes
```bash
git add .
git commit -m "describe your change"
git push origin main
```

### Pull remote changes
```bash
git pull origin main
```

---

## GitHub activity tracking bot

A scheduled bot captures GitHub activity (all commits on any branch, across personal and organization repos) and writes it into `github/` as per-day Markdown pages plus a weekly rollup. See `AGENTS.md` for how it works, or `scripts/` for the collector.

---

## Privacy & credential safety

- **No secrets are stored here.** No API keys, tokens, or credentials live in this repository.
- The GitHub bot uses your existing `gh` authentication (stored in your OS keyring), not a token in this repo.
- If you ever need to reference a credential here, replace it with `[REDACTED]`.
