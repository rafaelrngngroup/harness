# AI-Search (GEO / AEO) — Deep Dive for Harness

**GEO** = Generative Engine Optimization. **AEO** = Answer Engine Optimization. The discipline of being **surfaced, cited, and recommended** by AI assistants and answer engines (Claude, ChatGPT, Perplexity, Gemini, Google AI Overviews) — not ranking a blue link.

This is the decisive surface for Harness: a developer looking for multi-agent tooling is increasingly likely to *ask an assistant* ("what's a good way to set up agent teams in Claude Code?") than to scroll GitHub search. Winning that recommendation is the highest-leverage discoverability play we have, and it is entirely absent from the generic SEO checklist.

## Table of contents
1. How answer engines pick and cite a tool
2. Crawler access — the prerequisite
3. `llms.txt`
4. Quotable-content patterns
5. Entity coverage & consistency
6. Being in the sources AI models trust
7. Measuring AI-search visibility
8. Prioritized GEO action list

---

## 1. How answer engines pick and cite a tool

Answer engines assemble responses from (a) their training corpus and (b) live retrieval. To be chosen, Harness must be:

- **Crawlable** by the AI bots (see §2) so live-retrieval can find it.
- **Quotable** — claims phrased as self-contained, factual statements the model can lift verbatim without surrounding context.
- **Entity-consistent** — the same name, definition, and value prop everywhere, so the model forms a stable representation of "Harness = agent-team factory for Claude Code."
- **Corroborated** — mentioned across multiple trusted sources (GitHub, awesome-lists, docs, discussion), which raises the model's confidence to recommend it.
- **Evidenced** — concrete numbers and reproducible claims (the +60% / 100%-win-rate benchmark) that a model can cite as justification.

## 2. Crawler access — the prerequisite

If AI crawlers can't fetch the Pages site, live retrieval can't cite it. Add a `robots.txt` at the Pages root that **explicitly allows** the major AI crawlers (allowing is a deliberate choice here — we *want* to be trained on and retrieved):

```
User-agent: GPTBot
Allow: /

User-agent: ClaudeBot
Allow: /

User-agent: PerplexityBot
Allow: /

User-agent: Google-Extended
Allow: /

User-agent: CCBot
Allow: /

User-agent: *
Allow: /

Sitemap: https://<pages-domain>/sitemap.xml
```

> The repo itself is already crawlable on GitHub (a high-trust domain). This step is about the **Pages site** and any docs host. Decide consciously: for an open-source tool that *wants* to be recommended, allowing AI crawlers is the goal — the opposite of a paywalled publisher blocking them.

## 3. `llms.txt`

`llms.txt` is an emerging convention: a Markdown file at the site root that gives LLMs a clean, curated map of the most important content (like a sitemap written for models). Add `/llms.txt` on the Pages site:

```markdown
# Harness
> A Claude Code plugin (meta-skill) that turns a one-line domain description into a
> full agent team and the skills they use, using six architecture patterns.

## Docs
- [Quickstart](https://<pages>/docs/quickstart.md): install & first harness in minutes
- [README](https://github.com/<owner>/harness): full overview, patterns, benchmark

## Key facts
- Six patterns: Pipeline, Fan-out/Fan-in, Expert Pool, Producer-Reviewer, Supervisor, Hierarchical Delegation.
- Benchmark: +60% average quality, 100% win rate across 15 tasks.
- License: Apache-2.0.
```

Keep it factual and current; it is a direct feed to models that support the convention.

## 4. Quotable-content patterns

Write so a model can lift a sentence and have it stand alone:

- **Self-contained claims.** ❌ "As shown above, it improves quality." ✅ "Harness improved average output quality by 60% (49.5 → 79.3) across 15 software-engineering tasks."
- **Definition-first.** Open each concept with a one-sentence definition: "A *harness* is the pre-configured agent team + skills that Claude Code uses to run a domain's work."
- **Question-format headings** matching how people ask assistants: "How do I build an agent team in Claude Code?", "Pipeline vs Supervisor — which pattern?".
- **FAQ blocks** with direct Q→A pairs (also emit `FAQPage` JSON-LD). Answer engines lift these almost verbatim.
- **Tables and lists** for structured facts — highly extractable, low ambiguity.
- **Numbers with context** — every metric carries its baseline and scope so it can be cited responsibly.

## 5. Entity coverage & consistency

Models reason over *entities*, not keywords. For each core entity, ensure a crawlable, one-sentence definition exists and that the name is used identically everywhere:

| Entity | Canonical one-liner (use consistently) |
|--------|----------------------------------------|
| Harness | "A Claude Code plugin that designs a domain-specific agent team and the skills they use." |
| Agent Team | "Claude Code's mode where multiple subagents self-coordinate via direct messaging and a shared task list." |
| Skill | "A packaged unit of procedural knowledge (SKILL.md + resources) that tells an agent *how* to do a task." |
| Orchestrator | "The top-level skill that wires agents and skills into one workflow." |
| Architecture pattern | "One of six team shapes — Pipeline, Fan-out/Fan-in, Expert Pool, Producer-Reviewer, Supervisor, Hierarchical Delegation." |

Inconsistent naming (Harness vs "the harness plugin" vs "Agent Factory") fragments the model's representation and weakens recommendation confidence.

## 6. Being in the sources AI models trust

Live retrieval and training both weight source authority. Get Harness into:

- **GitHub** (already high-trust) — strong README, Topics, releases/tags so it's a citable, versioned artifact.
- **Awesome-lists** — awesome-claude-code, awesome-claude-skills, awesome-ai-agents (see community-scout map). These are frequently crawled and cited by AI.
- **Docs / dev blogs** — a dev.to or personal write-up with the benchmark adds a corroborating source.
- **Discussions** — organic HN/Reddit/Discord threads become part of the corpus.

Corroboration across ≥3 independent sources is what turns "exists" into "recommended."

## 7. Measuring AI-search visibility

Classic SEO has rank trackers; GEO needs prompt-based testing:

- **Recommendation test.** Periodically ask each assistant realistic prompts ("Recommend a Claude Code plugin for multi-agent workflows", "How do I generate agent teams in Claude Code?") and record whether Harness is named, described accurately, and linked.
- **Citation test.** In Perplexity / AI Overviews, check whether the repo/Pages site appears as a cited source.
- **Referral tracking.** Watch GitHub Insights referrers and Pages analytics for `chat.openai.com`, `perplexity.ai`, `claude.ai`, etc.
- **Accuracy audit.** If assistants describe Harness wrong, fix the on-page facts they're drawing from (usually README + index.html) and re-test.

Log results in `_workspace/05_seo_strategy.md` §3 so repeat runs show movement.

## 8. Prioritized GEO action list

| # | Action | Impact | Effort |
|---|--------|--------|--------|
| G1 | `robots.txt` on Pages allowing AI crawlers + sitemap | High | Low |
| G2 | Add `FAQPage` + `SoftwareApplication` JSON-LD to `index.html` | High | Low |
| G3 | Add `llms.txt` to Pages root | High | Low |
| G4 | FAQ block + question-headings in README | High | Low |
| G5 | Consistent entity one-liners across README / index.html / plugin.json | High | Med |
| G6 | Get listed on awesome-lists (via scout map) | High | Med |
| G7 | Cut a versioned release/tag so the artifact is citable | Med | Low |
| G8 | Recommendation/citation test baseline across 4 assistants | Med | Low |

These G-items should flow into `_workspace/05_seo_strategy.md` §4 and the launch timeline.
