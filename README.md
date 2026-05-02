# agentbrand-fit-corpus

Curated knowledge corpus for the **agentbrand.fit** tenant on Arlo Intelligence.

This repository is a deliberate staging ground for atoms — research, guides, transcripts, and reference material — that will be ingested into the tenant's Knowledge Substrate (L12) when SUB-001 Domain Harvest lands. Every file in this repo is structured to be ingestible without rework: provenance front-matter, consistent schemas, source attribution preserved.

The work compounds. Nothing committed here is throwaway.

---

## v1 Domain: Crimson Desert

The first and only domain in this corpus is Crimson Desert (Pearl Abyss, 2026). The agentbrand.fit tenant exists to validate the L12 substrate end-to-end on a low-stakes, closed-corpus domain before any client tenant touches the architecture.

The substrate test, stated plainly: when this corpus has been ingested, the Companion agent should be able to answer grounded, specific questions about Crimson Desert during a live gameplay session, surfacing maps and references inline, without hallucination.

If it can, the substrate works. If it can't, the gap has been found on a domain where the cost is zero.

---

## Repo Structure

- `README.md` — this file
- `_schema/atom-types.md` — front-matter convention. Read before committing.
- `guides/` — long-form written guides (pcgamer, gamesradar, other)
- `official/` — canonical sources (pearlabyss, steam)
- `community/` — community-sourced knowledge (reddit, forums)
- `videos/` — YouTube + streaming content (transcripts, notes)
- `research/` — raw outputs from external models (openai, gemini, grok, arlo)
- `assets/` — images, maps, screenshots
- `eval/test-questions.md` — retrieval test harness, the substrate eval

---

## Capture Workflow

When new content is added — scraped, manually written, or surfaced via an external model — it follows three rules:

1. **Markdown only.** No Word docs, no PDFs (transcribe them first), no Notion exports. Markdown is diffable, ingestible, and survives forever.
2. **Front-matter required.** Every file begins with the YAML block defined in `_schema/atom-types.md`. No exceptions. Atoms without provenance are atoms that get re-scraped later.
3. **One source per file.** Don't combine a Reddit thread and a YouTube transcript in the same file. The Librarian will file them as separate atoms; the repo should reflect that boundary.

When asking an external model for research, prompt it to produce markdown that is ready to commit — structured, sourced, no preamble.

---

## What This Repo Is Not

- **Not** a wiki. No editorial layer. No polished final guides. Source material only.
- **Not** the Companion. The Companion is a separate agent, lives on Arlo Intelligence, queries an indexed version of this corpus.
- **Not** an Arlo Inc. artifact. This corpus belongs to the agentbrand.fit tenant. Tenant isolation is honest from day one.
- **Not** public-facing in v1.

---

## Future Posture

agentbrand.fit is structured to grow into a multi-game hub — additional games added later as additional folders, same schema, same Companion + Librarian pattern. v1 does not pursue this; v1 only commits to not architecturally precluding it.

---

## Status

| Field | Value |
|---|---|
| Tenant | agentbrand.fit |
| v1 domain | Crimson Desert |
| Substrate readiness | L12 in build queue (after OBS-003 → L11) |
| Corpus status | Active capture phase |
| Owner | Adam Holwerda (Governor, Arlo Inc.) |
