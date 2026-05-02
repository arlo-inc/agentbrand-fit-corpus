# Research Prompt Template — agentbrand-fit-corpus

Use this template when asking any external model (OpenAI, Gemini, Grok, Arlo) to produce research for the Crimson Desert corpus. The output will arrive as a single ready-to-commit markdown file.

## How to Use

1. Copy the prompt block below
2. Replace the bracketed `[VARIABLES]` with your specific request
3. Paste into the model
4. The model returns a single markdown file
5. Save the file with a descriptive name in the appropriate folder (`research/openai/`, `research/gemini/`, `research/grok/`, or `research/arlo/`)
6. Commit to repo

No manual front-matter editing required. The model fills it in.

---

## The Prompt

You are producing research material for a structured knowledge corpus. Your output must be a single markdown file, ready to commit to a Git repository, with no preamble, no explanation, no chat-style intro or outro.

The corpus is for the **agentbrand.fit** tenant on Arlo Intelligence. The current domain is **Crimson Desert**, an open-world action-adventure game by Pearl Abyss released March 19, 2026.

### Output Format Requirements

Your entire response must be a single markdown file with this exact structure:

```
---
source_url: [the URL where you found this information, OR internal://[model-name]/[YYYY-MM-DD]-[topic-slug] if synthesized]
source_type: research_dump
captured_via: [openai | gemini | grok | arlo — pick the one matching you]
captured_at: [today's date in YYYY-MM-DD format]
domain: crimson_desert
tags: [list, of, snake_case, topic, tags]
title: "Human-readable title for this research"
notes: "Any caveats: contradictions you noticed, claims you couldn't verify, sources that disagreed, model limitations on this topic"
---

# [Title matching the title field above]

[Your research content, in clean markdown, with H2 / H3 sections as appropriate.]

[Cite specific sources inline where possible — e.g., "(per PC Gamer guide hub, May 2026)" or "(Reddit r/CrimsonDesert thread, top comment, April 2026)".]

[End with a "Sources" section listing every URL or reference you drew from.]

## Sources

- [URL or reference 1]
- [URL or reference 2]
- ...
```

### Content Requirements

- **Topic:** [INSERT YOUR SPECIFIC RESEARCH REQUEST HERE — e.g., "Hero Contribution mechanics: how the system works, how points are earned, what they unlock, optimal early-game strategy" or "Every legendary horse spawn location with coordinates and trigger conditions" or "Staglord boss fight: phases, attack patterns, parry windows, recommended gear and level"]

- **Depth:** Comprehensive. Cover primary mechanics, edge cases, common mistakes, and any patch-related changes if relevant.

- **Sourcing:** Cite as you go. If you cannot verify a claim against a real source, flag it inline with `[unverified]` and explain in the `notes:` front-matter field.

- **Conflicts:** If sources disagree, present both positions and flag in `notes:`. Do not arbitrarily pick a winner.

- **Tags:** Generate 4-8 specific snake_case tags relevant to the content. Examples of valid tag styles: `boss_fights`, `staglord`, `parry_timing`, `early_game`, `gear_progression`, `bloodstone`, `pailune`.

### What Not to Include

- No preamble ("Here's the research you asked for...")
- No outro ("Let me know if you'd like more detail...")
- No chat-style commentary
- No headers above the YAML front-matter
- No code-fence wrapper around the entire file (the file IS markdown — don't wrap it)
- No invented sources. If you don't have a source, say so in notes.

### One Final Check

Before responding, verify:
- [ ] YAML front-matter is the very first thing in the response
- [ ] All required front-matter fields are filled
- [ ] `captured_via` matches the model name
- [ ] `captured_at` is today's date
- [ ] Tags are snake_case and specific to the content
- [ ] Content has H1 title matching the `title` field
- [ ] A `## Sources` section exists at the end
- [ ] No preamble or outro outside the markdown structure

Now produce the research file.

---

## Example Filled-In Prompt

Below is the prompt with a specific topic filled in, ready to paste into a model:

> You are producing research material for a structured knowledge corpus. Your output must be a single markdown file, ready to commit to a Git repository, with no preamble, no explanation, no chat-style intro or outro.
>
> The corpus is for the agentbrand.fit tenant on Arlo Intelligence. The current domain is Crimson Desert, an open-world action-adventure game by Pearl Abyss released March 19, 2026.
>
> [...full prompt as above...]
>
> **Topic:** Hero Contribution system in Crimson Desert. Cover how reputation is earned in each region, what the contribution merchants sell, how the cap works, optimal regions to focus on for early-game gear, and any known exploits or patch-related changes through the latest update.
>
> Now produce the research file.

---

## Saving the Output

When the model returns the file, save it as a `.md` file in the appropriate folder:

- OpenAI / ChatGPT → `research/openai/[topic-slug].md`
- Gemini → `research/gemini/[topic-slug].md`
- Grok → `research/grok/[topic-slug].md`
- Arlo → `research/arlo/[topic-slug].md`

Filename convention: lowercase, hyphenated, descriptive. Examples:

- `hero-contribution-mechanics.md`
- `staglord-boss-fight.md`
- `legendary-horse-spawn-locations.md`
- `early-game-gear-progression.md`

---

## When to Bypass This Template

This template is for **research dumps** — synthesized model output. Use a different `source_type` when:

- Copying a specific guide article verbatim → use `source_type: guide_article`, save under `guides/[publisher]/`
- Transcribing a video → use `source_type: video_transcript`, save under `videos/transcripts/`
- Capturing a Reddit thread → use `source_type: reddit_thread`, save under `community/reddit/`

In those cases, fill in the front-matter manually using the schema in `_schema/atom-types.md`. The template above is specifically for asking models to produce original synthesized research.
