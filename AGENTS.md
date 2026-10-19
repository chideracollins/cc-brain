# AGENTS.md — cc-brain

Instructions for AI agents, tools, and future sessions working in this repository.

## What cc-brain is

cc-brain is the **Git-backed content source** for the user's GBrain personal knowledge base. It contains plain Markdown pages that GBrain syncs, embeds (via local Ollama `nomic-embed-text`, 768-dim), and indexes for semantic search. The repo is the human-readable, versioned layer; GBrain is the searchable layer on top.

- **Owner:** Collins Chidera Eze (GitHub: `chideracollins`)
- **Brain home:** `~/.gbrain`
- **GBrain source id:** `my-repo` (points at this directory)
- **Embedding:** local Ollama `nomic-embed-text` (768-dim), no API key needed
- **Autopilot:** launchd service `com.gbrain.autopilot`, pointed at `~/Repo/cc-brain`

## Working conventions

- **Write content, not scaffolding.** Pages are real notes, career evidence, or activity records — human-readable and factual.
- **Never put credentials in this repo.** No API keys, tokens, `.env`, or secrets. Redact anything sensitive as `[REDACTED]`. The GitHub bot uses `gh`'s OS-keyring auth, not a repo token.
- **Keep `.gbrain-bot/` out of the indexed knowledge.** It holds bot state (checkpoints) and must be excluded from GBrain ingestion and from being surfaced as knowledge pages.
- **Plain Markdown, clean frontmatter.** Follow GBrain conventions when adding pages (see the gbrain skill set under `~/.hermes/skills/gbrain/`).

## GitHub activity bot

A scheduled collector captures GitHub activity and writes it into `github/` as per-day Markdown pages plus a weekly rollup. It runs twice daily via a scheduled job.

**Behavior:**
- Captures **all commits on any branch** (not just `main`), across **personal repos and organization repos**.
- Primary source: per-repo commit history (`/repos/{owner}/{repo}/commits?author=…&since=…`) — no 90-day event cliff.
- Supplementary source: GitHub Events API for extras (stars, PRs, issues).
- Covers the user's 4 orgs where they are admin: `rapidClient`, `speech-code`, `Human-Language-Code`, `Storrs-LTD`.
- Includes a **one-time full-history backfill** from each repo's first commit to today.
- Deterministic, regenerable pages: each day's file is rebuilt in full from source; the checkpoint is an optimization, not the source of truth.
- **Re-captures the last 2 days** on every run to catch late pushes.
- Uses a fixed timezone (**Africa/Lagos**) for day boundaries (GitHub timestamps are UTC).
- Skips writing files for zero-activity days (records them in the checkpoint only).
- Produces a **weekly rollup** page (the primary thing users search).
- Reports failures loudly: nonzero exit on failure, status line, and a stale-checkpoint warning if not captured for ~2 days.
- Must never conflict with autopilot's own commits to this repo.

**Layout:**
- `github/activity/YYYY-MM-DD.md` — one page per active day
- `github/rollup/YYYY-Www.md` (or similar) — weekly summary
- `.gbrain-bot/checkpoint.json` — bot state (not indexed)

## Committing

- Commit with clear, conventional messages (e.g. `docs: capture what cc-brain is`).
- Push to `origin main`.
- Do not commit `.gbrain-bot/` checkpoint churn unless it is part of the bot's own scheduled write (the bot handles its own commits and must not loop with autopilot).

## Verification checklist for the bot

- Full backfill reaches the earliest commit in each repo (personal + org).
- No 90-day cliff: per-repo commit history is the primary source.
- Semantic search returns bot pages (test with a semantic query, not just keyword match).
- `.gbrain-bot/` and scripts are excluded from GBrain ingestion.
- Exit code is nonzero on failure; checkpoint staleness is surfaced.
