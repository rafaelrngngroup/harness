# Harness — SEO & AI-Discoverability Strategy
**Date:** 2026-07-24 · **Surfaces:** GitHub · Web · AI-search
**Owner agent:** seo-strategist · **Skill:** `seo-strategy`
**Inputs read:** `README.md`, `index.html`, `.claude-plugin/plugin.json`, `docs/quickstart.md`, `privacy.html`, `_workspace/01_auditor_repo_audit.md`, `_workspace/03_scout_outreach_map.md`

---

## 0. Verdict — do we already have this strategy?

**No — we do not yet have a dedicated, AI-ready SEO/discoverability strategy.** The only prior coverage is the repo-auditor's partial **"Discoverability" (7/10)** scoring in `_workspace/01_auditor_repo_audit.md`, which touches a handful of on-page/GitHub items (Topics, repo About, social preview, multilingual README) from a *trending-readiness* angle. That audit **flags**; it does not **prescribe** a search strategy, and it is silent on the three domains that matter most for a Claude Code plugin in 2026: **Technical SEO for the Pages site** (robots/sitemap/schema/canonical/CWV), **keyword & entity mapping**, and the decisive **AI-Search (GEO/AEO)** surface (crawler access, `llms.txt`, quotable claims, entity consistency).

**Adaptation summary.** A stock website-SEO checklist assumes a marketing site (Search Console, product pages, Google Business Profile, local SEO). Transplanting it wholesale wastes effort. This strategy **adapts** every classic item to our actual case — an open-source Claude Code plugin discovered on **GitHub**, on **Google** (repo + `index.html` Pages site + docs), and — most decisively — through **AI assistants** (Claude, ChatGPT, Perplexity, Gemini). The center of gravity shifts from "rank a blue link" to **"be the tool an AI recommends when a developer asks how to build agent teams in Claude Code."** Classic **Local SEO is N/A** and is **replaced** by Marketplace/Registry SEO; **AI-Search is added** as a new domain absent from generic checklists.

**Ground truth of current state (verified from files, 2026-07-24):**
- `index.html`: has `<title>` ("Harness — Agent Team & Skill Architect for Claude Code"); **NO** meta description, **NO** OG/Twitter cards, **NO** `rel=canonical`, **NO** Schema.org JSON-LD (grep confirmed 0 matches).
- **NO** `robots.txt`, **NO** `sitemap.xml`, **NO** `llms.txt` at repo root.
- `harness_banner.png` = **2.9 MB** (2,898,052 bytes) — a Core Web Vitals liability.
- `plugin.json` has a rich `keywords` array and consistent description.
- README is strong: entity-rich, FAQ block present, benchmark evidence, i18n (EN/KO/JA).
- GitHub **Topics** and repo **About** description are UI-set → **Unknown — verify in UI**.
- **Naming inconsistency detected:** README H1 / plugin.json = "Team-Architecture Factory"; `index.html` `<title>` + hero = "Agent Team & Skill Architect". This fragments the entity for LLMs (see §3 G5).

---

## 1. Scored checklist (7 domains)

State legend: **Have / Partial / Missing / Unknown (verify in UI) / N/A(reason)**. Surface: GitHub / Web (Pages+repo) / AI-search.

| Domain | Item | State | Surface | Impact | Effort | Owner |
|--------|------|-------|---------|--------|--------|-------|
| **1 Technical** | HTTPS enforced (GitHub Pages default) | Have | Web | Med | — | repo-auditor |
| 1 Technical | `robots.txt` on Pages (+ AI-crawler allow) | **Missing** | Web/AI-search | High | Low | seo-strategist |
| 1 Technical | `sitemap.xml` (index + docs + privacy) | **Missing** | Web | Med | Low | seo-strategist |
| 1 Technical | `rel=canonical` on `index.html` | **Missing** | Web | Med | Low | seo-strategist |
| 1 Technical | Schema.org JSON-LD (`SoftwareApplication` + `FAQPage`) | **Missing** | Web/AI-search | High | Low | seo-strategist |
| 1 Technical | Core Web Vitals — compress `harness_banner.png` (2.9 MB) | **Missing** | Web | High | Low | repo-auditor |
| 1 Technical | Mobile-friendly / responsive `index.html` | Have | Web | Med | — | repo-auditor |
| 1 Technical | Pages crawlable/indexable (no `noindex`); GitHub Pages live | Partial | Web | Med | Low | repo-auditor |
| 1 Technical | Register Pages site in GSC / Bing | **Missing** | Web | Med | Low | seo-strategist |
| 1 Technical | Server-log monitoring | N/A (managed host — use GitHub Insights + GSC) | — | — | — | — |
| **2 Keyword/Entity** | Primary + supporting keywords defined | Partial | All | High | Low | seo-strategist |
| 2 Keyword/Entity | Long-tail / conversational dev queries mapped | **Missing** | AI-search | High | Low | seo-strategist |
| 2 Keyword/Entity | Entities defined & crawlable (Claude Code, Agent Team, Skill…) | Partial | AI-search | High | Med | content-creator |
| 2 Keyword/Entity | Keywords mapped to owning pages | Partial | All | Med | Low | seo-strategist |
| 2 Keyword/Entity | Search intent (info/nav/transactional) mapped | Partial | All | Med | Low | seo-strategist |
| **3 On-Page** | `index.html` `<title>` keyword-rich | Have | Web | Med | — | — |
| 3 On-Page | `index.html` meta description | **Missing** | Web | High | Low | seo-strategist |
| 3 On-Page | GitHub Topics set (`claude-code`, `agent-teams`…) | **Unknown — verify in UI** | GitHub | High | Low | repo-auditor |
| 3 On-Page | Repo About description + website URL | **Unknown — verify in UI** | GitHub | High | Low | repo-auditor |
| 3 On-Page | Social preview image (1280×640) | **Missing** | GitHub | High | Low | repo-auditor |
| 3 On-Page | Image ALT text + compression on `harness_*.png` | Partial | Web/AI-search | Med | Low | content-creator |
| 3 On-Page | Single clear H1 (README + index.html) | Have | All | Low | — | — |
| 3 On-Page | Internal linking README ↔ docs ↔ index | Partial | All | Med | Low | content-creator |
| **4 Content** | Leads with a real problem / strong intro | Have | All | Med | — | — |
| 4 Content | Original data / benchmark evidence (E-E-A-T) | Have | All | High | — | content-creator |
| 4 Content | FAQ block in README | Have (3 Qs) | All/AI-search | High | Low | content-creator |
| 4 Content | Question-format headings ("How do I…") | Partial | AI-search | High | Low | content-creator |
| 4 Content | Well-defined entities (one-line defs) | Partial | AI-search | High | Med | content-creator |
| 4 Content | Consistent naming across surfaces | **Partial (conflict found)** | AI-search | High | Low | seo-strategist |
| 4 Content | Demo GIF / screencast | **Missing** | GitHub/Web | High | Med | content-creator |
| 4 Content | Clear CTAs (install / star / quickstart) | Have | All | Med | — | — |
| **5 Off-Page** | Awesome-list targets identified | Have (scout map) | GitHub/AI-search | High | — | community-scout |
| 5 Off-Page | Listed on awesome-claude-code / -skills | **Missing** | GitHub/AI-search | High | Med | community-scout |
| 5 Off-Page | Marketplace listing complete | Partial | Marketplace | High | Low | launch-strategist |
| 5 Off-Page | Editorial / newsletter mentions (TLDR, Console.dev) | **Missing** | Web/AI-search | Med | Med | community-scout |
| 5 Off-Page | Show HN / Product Hunt PR hook | **Missing** (templates ready) | Web | Med | Med | launch-strategist |
| 5 Off-Page | Consistent branded anchor text | Partial | All | Low | Low | community-scout |
| **6 AI-Search (GEO/AEO)** | AI-crawler access in `robots.txt` (GPTBot/ClaudeBot/PerplexityBot/Google-Extended/CCBot) | **Missing** | AI-search | High | Low | seo-strategist |
| 6 AI-Search | `llms.txt` at Pages root | **Missing** | AI-search | High | Low | seo-strategist |
| 6 AI-Search | `FAQPage` + `SoftwareApplication` JSON-LD | **Missing** | AI-search | High | Low | seo-strategist |
| 6 AI-Search | Quotable, self-contained claims (metric + baseline) | Have (exact phrasing block in README) | AI-search | High | — | content-creator |
| 6 AI-Search | Entity consistency across README/index/plugin.json | **Partial (conflict)** | AI-search | High | Low | seo-strategist |
| 6 AI-Search | Corroboration across ≥3 trusted sources | Partial | AI-search | High | Med | community-scout |
| 6 AI-Search | Versioned release/tag (citable artifact) | **Missing** (no tags per auditor) | GitHub/AI-search | Med | Low | repo-auditor |
| 6 AI-Search | Recommendation/citation test baseline (4 assistants) | **Missing** | AI-search | Med | Low | seo-strategist |
| **7 Marketplace/Registry** | Marketplace listing (icon, keyword-rich desc) | Partial | Marketplace | High | Low | launch-strategist |
| 7 Marketplace | Consistent name/desc/author (`plugin.json` ↔ `marketplace.json` ↔ README) | Partial | Marketplace | Med | Low | seo-strategist |
| 7 Marketplace | MCP registries / plugin directories listing | **Missing** | Marketplace/AI-search | Med | Med | community-scout |
| 7 Marketplace | Stars / testimonials / "Built with Harness" proof | Partial (Harness 100 section) | GitHub | Med | — | community-scout |
| 7 Marketplace | Classic Local SEO (GBP, NAP, maps) | N/A (open-source dev tool — replaced by this domain) | — | — | — | — |

---

## 2. Keyword & entity map

### Long-tail developer queries (what they type / ask an assistant)
| Query | Intent | Owning page/section |
|-------|--------|---------------------|
| "how to set up agent teams in Claude Code" | Informational | README Overview + `docs/quickstart.md` |
| "Claude Code multi-agent orchestration plugin" | Navigational/transactional | README H1 + repo About + index hero |
| "generate Claude Code agents from a prompt" | Informational | README Overview + Workflow section |
| "Claude Code skill architect / skill generator" | Informational | README Key Features + index features |
| "multi-agent workflow example Claude Code" | Informational | README Use Cases (8 prompts) |
| "pipeline vs supervisor agent pattern" | Comparative | README Architecture Patterns + patterns ref |
| "install Claude Code plugin marketplace" | Transactional | README Installation + `docs/quickstart.md` |
| "does structured pre-configuration improve LLM code quality" | Informational/evidence | README Research + `claude-code-harness` |
| "agent team factory / meta-skill Claude Code" | Navigational (brand-adjacent) | README H1 + plugin.json description |

Prioritize **low-competition, high-intent dev long-tails** over broad "AI agents" head terms.

### Entities (what LLMs reason over) — each needs a crawlable one-line definition, used identically everywhere
| Entity | Canonical one-liner (use verbatim across README / index.html / plugin.json) | Owning page |
|--------|------------------------------------------------------------------------------|-------------|
| **Harness** | "A Claude Code plugin that designs a domain-specific agent team and the skills they use, from a one-line prompt." | README H1, index hero, plugin.json |
| **Agent Team** | "Claude Code's mode where multiple subagents self-coordinate via direct messaging and a shared task list." | README Overview |
| **Skill** | "A packaged unit of procedural knowledge (SKILL.md + resources) telling an agent *how* to do a task." | README Key Features |
| **Orchestrator** | "The top-level skill that wires agents and skills into one workflow." | README Workflow |
| **Architecture pattern** | "One of six team shapes — Pipeline, Fan-out/Fan-in, Expert Pool, Producer-Reviewer, Supervisor, Hierarchical Delegation." | README Patterns table |
| **MCP / subagents / Claude Code** | Reference the canonical external definitions; link out for topical-authority signal. | README Requirements/links |

> **Consistency flag:** "Team-Architecture Factory" (README/plugin.json) vs "Agent Team & Skill Architect" (index.html title/hero) must be reconciled to one primary label with the other as a subtitle — pick one, use it in the H1, `<title>`, repo About, and marketplace desc identically. This is a High-impact / Low-effort GEO fix (G5).

---

## 3. AI-search (GEO/AEO) plan

Grounded in the G1–G8 action list from `references/ai-search-geo.md`. **All three foundational levers — `robots.txt` AI-crawler allow, `llms.txt`, and Schema.org — are Missing today**, so this is our single largest untapped upside.

**Crawler access (prerequisite).** No `robots.txt` exists. If AI crawlers can't fetch the Pages site, live retrieval can't cite it. Add a `robots.txt` at the Pages root that **explicitly allows** GPTBot, ClaudeBot, PerplexityBot, Google-Extended, CCBot, and `*` — for an open-source tool that *wants* to be recommended, allowing is the deliberate goal. Append the `Sitemap:` line. **(G1, High/Low)**

**Structured data.** `index.html` has zero JSON-LD. Add `SoftwareApplication` (name, description, author, license Apache-2.0, offers=free, applicationCategory=DeveloperApplication) + `FAQPage` (mirroring the README's 3 FAQ Q→As) + optional `BreadcrumbList`. High leverage for both Google rich results and AI extraction. **(G2, High/Low)**

**`llms.txt`.** Missing. Add `/llms.txt` at the Pages root — a curated Markdown map: one-line product definition, links to Quickstart + README, and a "Key facts" block (six patterns; +60% avg quality 49.5→79.3, 15/15 win-rate, −32% variance, n=15 author-measured; Apache-2.0). Direct feed to models supporting the convention. **(G3, High/Low)**

**Quotable content.** Already strong — the README carries the exact-phrasing block ("+60% avg quality (49.5 → 79.3), 15/15 win-rate, −32% variance (n=15, author-measured A/B, third-party replications pending)") and a 3-item FAQ. Extend with **question-format headings** ("How does Harness build an agent team?", "Pipeline vs Supervisor — which pattern?") to match how developers phrase prompts to assistants. **(G4, High/Low)**

**Entity coverage & consistency.** Definitions exist but naming is fragmented (see §2 flag). Reconcile to one canonical label + apply the one-liner table verbatim across README, `index.html`, and `plugin.json`. **(G5, High/Med)**

**Corroboration & citable artifact.** Get listed on awesome-claude-code / awesome-claude-skills (scout map is the backbone) to reach ≥3 independent trusted sources **(G6, High/Med)**; cut a versioned GitHub release/tag so the artifact is citable and versioned **(G7, Med/Low)**.

**Measurement.** Establish a baseline **recommendation/citation test** across Claude, ChatGPT, Perplexity, Gemini using realistic prompts ("Recommend a Claude Code plugin for multi-agent workflows"), record whether Harness is named/described accurately/linked, and watch GitHub Insights referrers for `chat.openai.com` / `perplexity.ai` / `claude.ai`. Log results here on each re-run. **(G8, Med/Low)**

---

## 4. Prioritized actions (impact × effort)

Ranked by impact ÷ effort; High-impact / Low-effort front-loaded.

| # | Action | Surface | Impact | Effort | Owner |
|---|--------|---------|--------|--------|-------|
| 1 | Set **GitHub Topics** (`claude-code`, `claude-code-plugin`, `agent-teams`, `multi-agent`, `orchestration`, `ai-agents`, `skills`) — verify/set in UI | GitHub | High | Low | repo-auditor |
| 2 | Set **repo About** description + website URL (Pages) — verify/set in UI | GitHub | High | Low | repo-auditor |
| 3 | Add **`index.html` meta description + `rel=canonical`** | Web | High | Low | seo-strategist |
| 4 | Add **Schema.org JSON-LD** (`SoftwareApplication` + `FAQPage`) to `index.html` (G2) | Web/AI-search | High | Low | seo-strategist |
| 5 | Add **`robots.txt`** on Pages allowing AI crawlers + `Sitemap:` (G1) | AI-search | High | Low | seo-strategist |
| 6 | Add **`llms.txt`** at Pages root (G3) | AI-search | High | Low | seo-strategist |
| 7 | Add **README FAQ expansion + question-format headings** (G4) | AI-search | High | Low | content-creator |
| 8 | **Compress `harness_banner.png`** (2.9 MB → WebP/optimized) for CWV | Web | High | Low | repo-auditor |
| 9 | **Reconcile entity naming** across README/index/plugin.json (G5) | AI-search | High | Low | seo-strategist |
| 10 | Upload **social preview image** (1280×640) via repo Settings | GitHub | High | Low | repo-auditor |
| 11 | Generate **`sitemap.xml`** + register Pages in GSC/Bing | Web | Med | Low | seo-strategist |
| 12 | Cut a **versioned release/tag** (citable artifact) (G7) | GitHub/AI-search | Med | Low | repo-auditor |
| 13 | **AI-search recommendation/citation baseline** across 4 assistants (G8) | AI-search | Med | Low | seo-strategist |
| 14 | Get listed on **awesome-claude-code / -skills** (scout map) (G6) | GitHub/AI-search | High | Med | community-scout |
| 15 | Add **demo GIF/screencast** after tagline | GitHub/Web | High | Med | content-creator |
| 16 | Complete **marketplace/registry listing** + MCP directory presence | Marketplace | Med | Med | launch-strategist |

Feed items 1–10 into the launch timeline as the pre-launch SEO block; 14–16 align with community-scout's outreach waves.

---

## 5. What changed since last run

**Initial run.** No prior `_workspace/05_seo_strategy.md` existed. Baseline established across all 7 domains; the repo-auditor's partial "Discoverability (7/10)" scoring was folded in (Topics, About, social preview) rather than re-audited. Next run: update AI-search recommendation-test results (G8), flip Unknown-in-UI items once verified, and mark completed actions.
