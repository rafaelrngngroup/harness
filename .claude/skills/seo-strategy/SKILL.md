---
name: seo-strategy
description: "Complete, AI-ready SEO & discoverability strategy adapted for the Harness case (a Claude Code plugin / open-source repo). Runs a scored audit across 7 domains — Technical SEO, Keyword & Entity Research, On-Page, Content Strategy (human + LLM), Off-Page Authority, AI-Search (GEO/AEO), and Marketplace/Registry SEO — then produces a prioritized action list. Use whenever the task involves 'SEO', 'discoverability', 'descoberta', 'ranquear/ranking', 'busca por IA / AI search', 'GEO', 'AEO', 'otimizar para LLM', 'palavras-chave/keywords', 'backlinks', 'GitHub Topics', 'social preview', 'checklist de SEO', or evaluating/improving how findable the project is on GitHub, Google, or AI assistants. Also trigger on follow-ups: 'atualiza a estratégia de SEO', 're-roda o SEO', 'melhora o SEO do repo'."
---

# SEO Strategy — AI-Ready Discoverability for Harness

A complete SEO checklist, **adapted from a generic website-SEO discipline to our actual case**: an open-source Claude Code plugin discovered on **GitHub**, **classic web search** (Google indexing the repo + the `index.html` Pages site + docs), and — most decisively — **AI assistants / answer engines** (Claude, ChatGPT, Perplexity, Gemini).

**Why adaptation matters.** A stock SEO checklist assumes a marketing website: Google Search Console, product pages, local SEO, a Google Business Profile. Transplanting it wholesale wastes effort. This skill maps every classic item to its GitHub / AI-search equivalent, or marks it N/A with a reason. The center of gravity shifts from "rank blue links" to **"be the tool an AI recommends when a developer asks for it."**

## When to use

- A user shares an SEO checklist/strategy and asks whether we have it or can improve it for our case.
- Any request to improve how findable Harness is on GitHub, Google, or AI assistants.
- Preparing or refreshing the launch (feeds content-creator and launch-strategist).
- Re-running/updating a prior strategy in `_workspace/05_seo_strategy.md`.

## The seven domains

Each domain is scored per item — **Have / Partial / Missing / N/A(reason)** — and every recommendation carries a **surface** (GitHub / Web / AI-search), **impact**, and **effort**. The exhaustive item-by-item checklist lives in `references/checklist-full.md`; load it when you need to score the repo line by line.

| # | Domain | Classic focus | Our-case center of gravity |
|---|--------|---------------|----------------------------|
| 1 | **Technical SEO** | crawlability, sitemap, CWV, schema | Pages-site indexability + crawler access for **AI bots** (GPTBot, ClaudeBot, PerplexityBot, Google-Extended) |
| 2 | **Keyword & Entity Research** | keywords, search intent | the **entities** LLMs reason over (Claude Code, Agent Teams, MCP, skills) + long-tail dev queries |
| 3 | **On-Page** | titles, meta, H1, URLs | repo description + **GitHub Topics** + README structure + `index.html` meta |
| 4 | **Content Strategy** | helpful content, E-E-A-T | content written to be **quoted by LLMs**: entity defs, FAQ blocks, question-headings, benchmark proof |
| 5 | **Off-Page Authority** | backlinks, digital PR | **awesome-lists**, editorial mentions, natural anchors (backbone = community-scout map) |
| 6 | **AI-Search (GEO/AEO)** | *(absent from classic checklists)* | **the new discipline** — being cited/recommended by answer engines. See `references/ai-search-geo.md` |
| 7 | **Marketplace/Registry SEO** | *(replaces Local SEO)* | plugin marketplace + MCP registry listing, description, keywords, canonical NAP-equivalent |

> Domains 1–5 are the image's checklist, adapted. Domain 6 is **added** because it is the decisive surface for a dev tool and absent from generic checklists. Domain 7 **replaces** classic "Local SEO", which is N/A here.

## Workflow

### Step 0 — Context check
Read `_workspace/05_seo_strategy.md` if it exists (improve deltas, don't restart). Read the repo-auditor discoverability findings (`_workspace/01_auditor_repo_audit.md`) and the community-scout map (`_workspace/03_scout_outreach_map.md`) to avoid re-auditing what's already known.

### Step 1 — Score the checklist
Walk `references/checklist-full.md` domain by domain. For each item, inspect the actual repo state (README, `index.html`, `plugin.json`, `docs/`, `.github/`) and mark one of the **five canonical states** — use this legend verbatim everywhere (schema, checklist, agent output):

> **Have / Partial / Missing / Unknown-verify-in-UI / N/A(reason)**

Never assume Done for anything set via the GitHub UI (repo About description, Topics, social preview) — mark **Unknown-verify-in-UI** and add a low-effort verification action.

**Pages-dependency gate:** many Technical (§1) and AI-search (§6) items depend on the GitHub Pages site actually being live (robots.txt, sitemap.xml, llms.txt, canonical, Schema.org all live *on* the Pages site). If Pages deployment is unverified — the repo has an `index.html` but nothing confirms it is deployed — do **not** score those items **Have**; mark them **Partial** or **Missing**, keep the actions, and flag "gated on Pages deployment" so the dependency is explicit.

### Step 1.5 — Diff the product identity across surfaces
Before scoring content/entity items, actively **diff the product name and tagline** across `README.md` (H1), `index.html` (`<title>` + hero), `plugin.json`/`marketplace.json` (name/description). Inconsistent naming fragments the entity an LLM builds ("Team-Architecture Factory" vs "Agent Team & Skill Architect" are *not* the same entity to a model) and directly weakens AI-recommendation confidence. Record any mismatch as a High-impact / Low-effort finding feeding domain 4 (Content) and domain 6 (GEO/AEO, G5). This catch must be deliberate, not accidental.

### Step 2 — Build the keyword-entity map
Produce two lists:
- **Long-tail developer queries** (what they type): e.g. "Claude Code multi-agent setup", "generate agent teams from a prompt", "Claude Code skill architect".
- **Entities** (what LLMs reason over): Claude Code, Agent Teams, subagents, skills, MCP, orchestration patterns. Map each to the page/section that should own it. Detail in `references/checklist-full.md` §2.

### Step 3 — Apply the AI-search layer
Load `references/ai-search-geo.md`. Check: crawler access for AI bots, quotable claims, `llms.txt`, structured entity definitions, presence in the sources AI models cite (GitHub, awesome-lists, docs). This is where our biggest upside is.

### Step 4 — Prioritize
Rank all Missing/Partial items by **impact × (1/effort)**. Front-load High-impact / Low-effort wins (repo description, Topics, Schema.org on `index.html`, FAQ block in README, AI-bot crawl access). Assign each action an owner agent from the launch-team roster: **seo-strategist** (strategy, technical/AI-search levers), **content-creator** (copy, FAQ, entity defs, demo assets), **repo-auditor** (repo/UI settings, CWV, releases), **community-scout** (off-page: awesome-lists, registries, editorial mentions), **launch-strategist** (sequencing into the launch timeline, marketplace listing).

### Step 5 — Emit the strategy
Write `_workspace/05_seo_strategy.md` using the output schema below.

## Output schema — `_workspace/05_seo_strategy.md`

```markdown
# Harness — SEO & AI-Discoverability Strategy
**Date:** {YYYY-MM-DD} · **Surfaces:** GitHub · Web · AI-search

## 0. Verdict — do we already have this strategy?
{1 paragraph: what exists today, what's missing, adaptation summary}

## 1. Scored checklist (7 domains)
State legend (use verbatim): Have / Partial / Missing / Unknown-verify-in-UI / N/A(reason). Group rows by domain.
| Domain | Item | State | Surface | Impact | Effort | Owner |
|--------|------|-------|---------|--------|--------|-------|
...

## 2. Keyword & entity map
### Long-tail developer queries
### Entities (for LLM reasoning)

## 3. AI-search (GEO/AEO) plan
{crawler access, quotable claims, llms.txt, entity coverage}

## 4. Prioritized actions (impact × effort)
| # | Action | Surface | Impact | Effort | Owner |
...

## 5. What changed since last run
{delta vs prior _workspace/05_seo_strategy.md, or "initial"}
```

## Guardrails

- **Adapt or mark N/A — never force.** If a classic item has no honest mapping (Google Business Profile, store locator), mark N/A with a one-line reason. A padded checklist is worse than a truthful one.
- **AI-citability beats keyword stuffing.** When on-page choices conflict, favor self-contained, entity-rich, factual statements an LLM can quote verbatim over repetitive keyword density.
- **Proof, not adjectives.** E-E-A-T for us is the benchmark evidence, the reproducible experiment, the changelog, real authorship. Never invent metrics or claims.
- **Stay lean.** This SKILL.md is the map; the full per-item checklist and the GEO deep-dive live in `references/` and load only when needed.

## References

- `references/checklist-full.md` — the exhaustive item-by-item checklist (all 7 domains), each item mapped from the generic SEO discipline to our case with keep / adapt / replace / N/A.
- `references/ai-search-geo.md` — the GEO/AEO deep dive: how AI assistants pick and cite tools, crawler access, `llms.txt`, quotable-content patterns, and how to measure AI-search visibility.
