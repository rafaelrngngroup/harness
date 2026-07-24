# G8 — AI-Search / Recommendation Baseline (the "before" measurement)

**Project:** Harness (Claude Code agent-team & skill architect)
**Owner agent:** seo-strategist · **Action:** G8 (from `_workspace/05_seo_strategy.md` §3/§4)
**Snapshot date:** 2026-07-24
**Query set source:** `_workspace/05_seo_strategy.md` §2 (keyword & entity map) + 2 brand queries.

---

## Method & caveats (read first)

1. **Classic-search is a PROXY, not the real target.** This baseline measures **classic web-search visibility** (Google-style results via WebSearch) because that is what is executable from this environment. It is a *correlate of*, **not identical to**, whether a generative assistant (Claude/ChatGPT/Perplexity/Gemini) will *name and recommend* Harness. Live-retrieval assistants draw on indexed pages, so classic visibility is a leading indicator — but the recommendation test in §4 must be run manually to measure the real GEO/AEO outcome. Treat §1–§3 as measured, §4 as a template to be executed.

2. **Generative assistants were NOT queried.** This environment cannot call Claude/ChatGPT/Perplexity/Gemini. **No assistant answers are fabricated.** §4 is a ready-to-run prompt+scoring template for a human to execute, with an empty results table.

3. **Fork vs upstream — the identity that matters most here.** "Harness" is a shared name across a family of repos. Every result below is tagged with WHICH property it is:
   - **UPSTREAM** = `revfactory/harness` (the canonical repo: **8,491★**, 1,157 forks, topics already set, Pages live & indexed). This holds all the search equity.
   - **FORK** = `rafaelrngngroup/harness` (our fork — the subject of the strategy). Assumed Pages host: `https://rafaelrngngroup.github.io/harness/`.
   - **SISTER** = `revfactory/claude-code-harness`, `dadwadw233/claude-code-harness`, `Chachamaru127/claude-code-harness` etc. (different projects that share the word "harness").
   - **PORT** = `meta-harness` (Codex port — not observed in results this run).

4. **Environment limitation on Pages fetch.** The agent proxy **denies CONNECT to `*.github.io`** (gateway returns 403 — confirmed via `$HTTPS_PROXY/__agentproxy/status`, `kind: connect_rejected`). So neither Pages site could be fetched directly (WebFetch and curl both blocked at the gateway, not a real 404). Pages liveness is therefore inferred from **search indexation** (does the URL appear as an indexed result), not from a direct 200. Stated explicitly wherever it affects a conclusion.

5. **GitHub search excludes forks by default.** `search_repositories` for `user:rafaelrngngroup harness` returned **0** — this is expected API behavior for forks (they're hidden from repo search unless they out-star the parent), **not** proof the fork is absent. Reported as-is, not over-interpreted.

---

## §1 — Classic web-search visibility (measured 2026-07-24)

10 queries: 8 long-tail/problem-space (from §2) + 2 brand. For each: does any Harness property appear in the top results, which one, its approximate rank, and what outranks it.

| # | Query | Type | Harness in top results? | Which property (rank) | Outranked by / competing sources |
|---|-------|------|------------------------|----------------------|----------------------------------|
| 1 | how to set up agent teams in Claude Code | long-tail | **No** | — | Anthropic docs, Medium (darasoba, kargarisaac), SitePoint, claudefa.st, Substack |
| 2 | Claude Code multi-agent orchestration plugin | long-tail | **No** | — | oh-my-claudecode, zircote/claude-team-orchestration, barkain, codehornets, mbruhler, wshobson/agents |
| 3 | generate Claude Code agents from a prompt | long-tail | **No** | — | anthropics/claude-code, Piebald-AI, Anthropic docs, claudecodeagents.com |
| 4 | Claude Code skill architect skill generator | long-tail | **No** | — | mcpmarket skill-architect, claude.com skill-creator, Anthropic docs, arXiv papers |
| 5 | multi-agent workflow example Claude Code agent team | long-tail | **No** | — | MindStudio, aws-samples, Medium, alexop.dev, EPAM |
| 6 | pipeline vs supervisor agent pattern Claude Code | long-tail | **No** | — | alphasignal, MindStudio, agentpatterns.ai, digitalapplied |
| 7 | does structured pre-configuration improve LLM code quality benchmark | long-tail | **No** | — | arXiv papers only (no product surfaced — pure academic SERP) |
| 8 | agent team factory meta-skill Claude Code | long-tail | **Yes** | **UPSTREAM** Pages `revfactory.github.io/harness/` (~#3) + **UPSTREAM** repo (~#4) | mcpmarket skill-and-agent-factory (#1), github topics/meta-skill (#2) |
| 9 | Harness Claude Code plugin | **brand** | **Yes** | Independent **DEV.to** article on *our* Harness (~#2) | SISTER `dadwadw233/claude-code-harness` (#1); claudepluginhub listings for *other* harnesses |
| 10 | Harness agent team architect Claude Code | **brand** | **Yes** | **UPSTREAM** Pages `revfactory.github.io/harness/` (**#1**), DEV.to (#2), **UPSTREAM** repo (#5), skillsllm.com/skill/harness (#6) | MindStudio, WaveSpeed (generic "agent harness" explainers) |

### What the table says

- **Long-tail / problem-space capture: 1 of 8.** Harness surfaces only for query #8 ("agent team factory meta-skill"), which is already a near-brand phrase. For the 7 genuinely generic developer queries (how-to, orchestration plugin, generate agents, skill architect, workflow example, pattern comparison, benchmark), **Harness does not appear at all** — the space is owned by Anthropic docs, Medium/Substack tutorials, and competitor plugins (oh-my-claudecode, claude-team-orchestration, wshobson/agents).
- **Brand capture: 2 of 2.** If a developer already knows the name "Harness," they find it (best rank **#1**, the upstream Pages site).
- **Every surfaced property is UPSTREAM or independent-editorial-about-upstream.** The **fork (`rafaelrngngroup`) appears in ZERO results** across all 10 queries. All search equity — the #1 ranking, the repo, the directory listing — accrues to `revfactory`. The fork currently has no independent classic-search footprint.

---

## §2 — Indexation & Pages-live check

| Property | Indexed / live? | Evidence | Note |
|----------|-----------------|----------|------|
| **UPSTREAM repo** `github.com/revfactory/harness` | **Yes — live & indexed** | 8,491★ via GitHub API; appears in SERP for queries #8, #10 | Topics already set: `claude-code`, `claude-code-plugin`, `harness`, `harness-engineering` |
| **UPSTREAM Pages** `revfactory.github.io/harness/` | **Yes — live & indexed** | Ranks **#1** for brand query #10, ~#3 for #8; title indexed as "Harness — Agent Team & Skill Architect for Claude Code" | Could not fetch body (proxy blocks `*.github.io`), but indexation confirms it is live |
| **FORK Pages** `rafaelrngngroup.github.io/harness/` | **Not confirmed live; zero indexation evidence** | Absent from all 10 SERPs; direct fetch blocked by proxy gateway (403 CONNECT, not a real 404) | **Validates the strategy's Pages-dependency gate as a real risk.** The `robots.txt`/`llms.txt`/`sitemap.xml`/canonical/OG URLs written in §5 of the strategy all assume this host — if Pages isn't enabled here (or a custom domain is used), those assets resolve to nothing and G1/G2/G3 produce no measurable effect. **Verify Pages is enabled + indexed in the GitHub UI before claiming any GEO win.** |
| **FORK repo** `github.com/rafaelrngngroup/harness` | **Unverifiable via search** | `search_repositories user:rafaelrngngroup` → 0 results | Expected: GitHub repo-search hides forks by default. Not evidence of absence — confirm existence/visibility in UI. |

**Bottom line for §2:** Upstream Pages is live and dominant. **The fork's Pages — the entire delivery surface the strategy's technical/GEO actions target — shows no indexation and could not be verified live from here.** This is a prerequisite blocker, not a nice-to-have.

---

## §3 — Corroboration source count (GEO target ≥ 3)

Independent, trusted sources that currently mention/link the Harness *entity* (the agent-team architect), observed in this run:

| Source | Type | Independent of owner? | About which property |
|--------|------|----------------------|----------------------|
| `github.com/revfactory/harness` | Canonical repo | Owner-controlled (not independent) | UPSTREAM |
| `revfactory.github.io/harness/` | Landing page | Owner-controlled (same entity) | UPSTREAM |
| `dev.to/arshtechpro/harness-turn-a-one-line-prompt-into-a-full-agent-team-for-claude-code` | Editorial blog | **Yes — independent** | Describes *our* Harness accurately |
| `skillsllm.com/skill/harness` | Aggregator/directory ("AI Agents on GitHub, 8.4k★") | **Yes — independent** | UPSTREAM (pulls repo metadata) |

**Count:**
- **Independent third-party sources = 2** (dev.to editorial, skillsllm directory).
- **Total distinct trusted sources incl. owned canonical = 3** (GitHub repo + the 2 independent).
- **Against the ≥3 independent-source GEO target: NOT yet met (2/3).**
- **For the FORK specifically: 0 independent sources.** Every corroboration point references upstream. The fork inherits none of it.

Not counted (do not corroborate our entity): `claudepluginhub.com` listings (they index *other* "harness"-named plugins — panayiotism-claude-harness, browser-use, alan-ift harness-kit), and the SISTER `claude-code-harness` repos. Counting these would inflate the number dishonestly.

---

## §4 — Generative-assistant recommendation test (TEMPLATE — not executed)

**Why a template:** this environment cannot query the assistants, and inventing answers would violate the honesty rules. Run this manually (fresh/incognito session per assistant, default model, no custom instructions) and paste results back here on the next G8 re-run.

### Prompt set (5 realistic developer prompts)

- **P1 (open recommendation):** "Recommend a Claude Code plugin for building multi-agent workflows."
- **P2 (how-to intent):** "How do I set up agent teams in Claude Code? Is there a tool that generates the team for me?"
- **P3 (category, competitive):** "What are the best tools to design a team of specialized agents and their skills in Claude Code?"
- **P4 (problem-first, no brand):** "I want to turn a one-line description into a full agent team with skills and an orchestrator in Claude Code — what should I use?"
- **P5 (brand probe):** "What is Harness for Claude Code, who makes it, and what does it do?"

### Scoring rubric (per assistant × prompt cell)

- **Named?** (Y/N) — did the answer mention Harness by name?
- **Which repo?** (upstream `revfactory` / fork `rafaelrngngroup` / sister / unclear) — critical: does it point to *us*?
- **Described accurately?** (Y/N) — meta-skill that designs an agent team + skills from one prompt; 6 patterns; Apache-2.0. No hallucinated features.
- **Linked?** (Y/N) — did it give a URL, and to which property?
- **Rank/position** — 1st tool named / in a list / only after brand probe / not at all.
- **Notes** — competitors named ahead of it; caveats; hallucinations.

### Empty results table — fill on execution

| Prompt | Assistant | Named? | Which repo? | Accurate? | Linked? | Position | Notes |
|--------|-----------|--------|-------------|-----------|---------|----------|-------|
| P1 | Claude | | | | | | |
| P1 | ChatGPT | | | | | | |
| P1 | Perplexity | | | | | | |
| P1 | Gemini | | | | | | |
| P2 | Claude | | | | | | |
| P2 | ChatGPT | | | | | | |
| P2 | Perplexity | | | | | | |
| P2 | Gemini | | | | | | |
| P3 | Claude | | | | | | |
| P3 | ChatGPT | | | | | | |
| P3 | Perplexity | | | | | | |
| P3 | Gemini | | | | | | |
| P4 | Claude | | | | | | |
| P4 | ChatGPT | | | | | | |
| P4 | Perplexity | | | | | | |
| P4 | Gemini | | | | | | |
| P5 | Claude | | | | | | |
| P5 | ChatGPT | | | | | | |
| P5 | Perplexity | | | | | | |
| P5 | Gemini | | | | | | |

**Score = # of (Named=Y AND points to our intended property) cells ÷ 20.** Track the "Which repo?" column tightly — if assistants name Harness but link **upstream**, the fork gains awareness but no traffic/attribution. Also watch GitHub Insights → Traffic → Referrers for `chat.openai.com`, `perplexity.ai`, `claude.ai`, `gemini.google.com` as an independent corroborating signal.

---

## §5 — Baseline scorecard (AS OF 2026-07-24)

| Metric | Baseline value | Notes |
|--------|----------------|-------|
| Long-tail queries where any Harness property appears | **1 / 8** | Only #8, itself near-brand |
| Brand queries where Harness appears | **2 / 2** | Best rank **#1** (upstream Pages) |
| All queries combined | **3 / 10** | |
| Best organic rank achieved | **#1** | UPSTREAM Pages, brand query only |
| Best rank on a *non-brand* query | ~**#3** | UPSTREAM Pages, query #8 |
| Queries surfacing the **FORK** (`rafaelrngngroup`) | **0 / 10** | Fork has no classic-search footprint |
| Independent corroborating sources | **2** (target ≥3) | dev.to, skillsllm; +1 owned canonical = 3 total |
| Independent sources for the fork specifically | **0** | |
| UPSTREAM Pages live & indexed | **Yes** | |
| FORK Pages live & indexed | **No / unverified** | Absent from SERPs; proxy blocked direct fetch — verify in UI |
| Generative-assistant recommendation score | **Not measured** | §4 template pending manual run |
| GitHub stars (equity reference) | UPSTREAM 8,491★ · FORK n/a | Search equity concentrated upstream |

### What a good "after" looks like (re-run targets)

- Long-tail capture **≥ 3 / 8** (Harness appears for genuine problem-space queries, not just its own name).
- **The FORK surfaces in ≥ 1 result**, OR a deliberate decision is recorded to consolidate equity into upstream (so movement is attributable to *something we own*).
- Independent corroborating sources **≥ 3** (add awesome-claude-code / awesome-claude-skills listing → G6).
- FORK Pages **confirmed live & indexed** with `robots.txt` + `llms.txt` + JSON-LD fetchable (unblocks G1/G2/G3 measurement).
- Generative-assistant recommendation score **> 0/20 with accurate description**, and at least one assistant links the intended property.
- At least one AI referrer visible in GitHub Insights.

---

## Single highest-leverage gap this baseline reveals

**Harness is invisible for the problem-space queries developers actually type (1/8 long-tail), and what visibility exists belongs entirely to the upstream `revfactory` repo — the fork has a zero footprint and its own Pages surface is unverified/unindexed.** The tool is only found by people who already know its name. The fork-vs-upstream split means that until (a) the fork's Pages is confirmed live and indexed and (b) a decision is made on whether to build the fork's own identity or route equity to upstream, the G1/G2/G3 technical GEO assets can't produce a *measurable, attributable* movement. Closing the non-brand-query gap (content/GEO for "how to set up agent teams," "multi-agent orchestration plugin," "generate agents from a prompt") is the largest untapped upside — but it is gated on resolving the Pages-liveness prerequisite first.
