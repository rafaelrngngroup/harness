# Full SEO Checklist — Mapped to the Harness Case

Every item below is taken from the generic "AI-ready SEO checklist" and given a **disposition** for our case (a Claude Code plugin / open-source GitHub repo + `index.html` Pages site + docs):

- **KEEP** — applies almost as-is.
- **ADAPT** — applies, but the concrete action changes for GitHub / a repo.
- **REPLACE** — the classic item is N/A; its *authority equivalent* takes its place.
- **N/A(reason)** — genuinely not applicable; do not create busywork.

Score each item with one of the five canonical states (used identically in SKILL.md and the agent output): **Have / Partial / Missing / Unknown-verify-in-UI / N/A(reason)**. Items that live on the GitHub Pages site are **gated on Pages being live** — if deployment is unverified, score them Partial/Missing, never Have.

## Table of contents
1. Technical SEO
2. Keyword & Entity Research
3. On-Page SEO
4. Content Strategy (human + LLM)
5. Off-Page Authority
6. AI-Search (GEO/AEO) — see `ai-search-geo.md`
7. Marketplace/Registry SEO (replaces Local SEO)

---

## 1. Technical SEO

| Classic item | Disposition | Our-case action |
|--------------|-------------|-----------------|
| Set up Google Search Console + Bing Webmaster | **ADAPT** | Register the **GitHub Pages site** (from `index.html`) in GSC/Bing. The repo itself is indexed via GitHub; track it with GitHub Insights (traffic/referrers). |
| Set up Google Analytics 4 | **ADAPT** | Add privacy-friendly analytics to the Pages site only (or Plausible). Respect the existing `privacy.html`. Repo traffic → GitHub Insights. |
| Create & submit XML sitemap | **ADAPT** | Generate `sitemap.xml` for the Pages site (index + docs + privacy). Submit in GSC. |
| Create & submit robots.txt | **ADAPT** | Add `robots.txt` for the Pages site — **and explicitly allow AI crawlers** (see §6). |
| Enable HTTPS | **KEEP** | GitHub Pages is HTTPS by default — verify enforced. |
| Ahrefs/SEMrush Webmaster Tools | **KEEP (optional)** | Nice-to-have for backlink monitoring of the Pages site; low priority. |
| Fix manual actions in GSC | **KEEP** | Monitor once GSC is connected. |
| Pages crawlable & indexable | **ADAPT** | Ensure `index.html`, `docs/*`, `privacy.html` are linked and not `noindex`. README is indexed by GitHub. |
| Fix broken links & orphan pages | **KEEP** | Lint README + docs links; ensure every doc is linked from README or index. |
| Remove redirect chains | **KEEP** | Check any shortlinks used in outreach. |
| Optimize & monitor Core Web Vitals (CrUX) | **KEEP** | `index.html` must be fast — inline critical CSS, compress the banner (`harness_banner.png` is ~2.9 MB → serve a web-optimized/WebP version). |
| Mobile-friendly | **KEEP** | Verify the landing page's responsive layout + i18n toggle on mobile. |
| Canonical tags implemented | **ADAPT** | Add `<link rel="canonical">` to `index.html`; point repo README canonical intent at the GitHub URL. |
| Implement relevant Schema.org | **ADAPT** | Add `SoftwareApplication` / `SoftwareSourceCode` + `FAQPage` + `BreadcrumbList` JSON-LD to `index.html`. High leverage for both Google rich results and AI extraction. |
| Validate all schemas | **KEEP** | Run Rich Results Test on `index.html`. |
| Consistent structured data | **KEEP** | Keep name/description/author identical across `plugin.json`, README, `index.html` schema. |
| Verify indexation of important pages | **ADAPT** | `site:` check the Pages site; confirm repo appears for brand query "Harness Claude Code". |
| Monitor server logs for errors | **N/A** | GitHub Pages/host is managed. Use GitHub Insights + GSC coverage report instead. |

**Top technical wins for us:** compress the banner (CWV), add Schema.org + canonical to `index.html`, add `robots.txt`/`sitemap.xml` with AI-crawler allow, register the Pages site in GSC.

---

## 2. Keyword & Entity Research

| Classic item | Disposition | Our-case action |
|--------------|-------------|-----------------|
| Find primary & supporting keywords | **KEEP** | Primary: "Claude Code agent teams", "Claude Code plugin", "multi-agent orchestration". Supporting: "skill architect", "agent scaffolding", "subagents". |
| Include long-tail & conversational keywords | **ADAPT** | Developer long-tails: "how to set up agent teams in Claude Code", "generate Claude Code skills from a prompt", "Claude Code multi-agent workflow example". |
| Identify real user questions | **KEEP** | Mine from Claude Code Discord, GitHub issues, Reddit r/ClaudeAI, HN threads. |
| Analyze competitor keywords | **ADAPT** | "Competitors" = other Claude Code plugins / agent frameworks; see their Topics & README terms. |
| Map search intent to keywords | **KEEP** | Informational (README/docs), navigational (brand), transactional (install / marketplace). |
| Group keywords into topics/clusters | **KEEP** | Clusters: *agent teams*, *skills*, *orchestration patterns*, *benchmarks/evidence*. |
| **Map entities beyond keywords** | **ADAPT (critical)** | Entities LLMs reason over: **Claude Code, Agent Teams, subagents, skills, MCP, orchestration patterns (Pipeline / Fan-out / Expert Pool / Producer-Reviewer / Supervisor / Hierarchical)**. Each entity must be *defined* somewhere crawlable. |
| Map keywords to pages | **ADAPT** | README = primary cluster; `docs/quickstart.md` = install intent; `index.html` = brand + value prop. |
| Prioritize by ranking potential & traffic | **KEEP** | Favor low-competition, high-intent dev long-tails over broad "AI agents". |

**Deliverable:** the keyword-entity map in `_workspace/05_seo_strategy.md` §2.

---

## 3. On-Page SEO

| Classic item | Disposition | Our-case action |
|--------------|-------------|-----------------|
| URLs short, clean, descriptive, keyworded | **ADAPT** | Doc filenames & anchors descriptive; Pages URLs clean. |
| One primary keyword per page | **KEEP** | README ← "Claude Code agent teams"; quickstart ← "install / setup". |
| Optimize titles for CTR + AI | **ADAPT** | Repo **description** (About) + `index.html <title>` = keyword-rich, benefit-led. |
| Optimize meta descriptions | **ADAPT** | `index.html` meta description; repo About text. |
| H1 used once, clearly | **KEEP** | One H1 on `index.html`; README top heading is the H1-equivalent. |
| Keywords appear naturally | **KEEP** | In README intro, feature list, docs — no stuffing. |
| Optimize images (name, ALT, caption, compression) | **KEEP** | Rename/compress `harness_*.png`; add ALT text; the ALT is also read by AI crawlers. |
| Strategic internal links by cluster | **KEEP** | README ↔ docs ↔ index.html cross-links; link each orchestration pattern to its reference. |
| Breadcrumbs for navigation & SEO | **ADAPT** | Breadcrumb JSON-LD on `index.html`; docs nav in README ToC. |
| External links to trustworthy sources | **KEEP** | Link Claude Code docs, MCP spec — signals topical authority. |
| **GitHub Topics** *(repo-specific, not in image)* | **ADD** | Set Topics: `claude-code`, `claude-code-plugin`, `agent-teams`, `multi-agent`, `orchestration`, `ai-agents`, `skills`. Primary GitHub discovery lever. |
| **Repo About description + website URL** *(repo-specific)* | **ADD** | Set About text (keyword-rich) + website = Pages URL. High-impact / low-effort. |

---

## 4. Content Strategy (Human + LLM)

| Classic item | Disposition | Our-case action |
|--------------|-------------|-----------------|
| Content resolves a real problem | **KEEP** | Lead README with the pain: "2-hour yak shave to wire a multi-agent workflow." |
| Strong introduction | **KEEP** | First 3 lines must state what Harness is + the outcome. |
| Original insights & data | **KEEP** | The +60% / 100%-win-rate benchmark is our differentiator — keep it prominent & reproducible. |
| Cover the topic completely | **KEEP** | Document all 6 orchestration patterns, agent vs skill, progressive disclosure. |
| Titles/subtitles structured for AI | **KEEP** | Descriptive, hierarchical headings; AI extracts these as structure. |
| Question-format headings | **ADAPT** | Add "How does Harness build an agent team?", "When should I use Fan-out vs Supervisor?" — matches AI query phrasing. |
| Write for humans AND LLMs | **KEEP (core)** | Self-contained, quotable sentences; define entities inline; avoid "as shown above" references a crawler can't resolve. |
| Demonstrate E-E-A-T (authorship, sources, experience) | **ADAPT** | Named author, linked experiment methodology, changelog, real GitHub history = our E-E-A-T. |
| Well-defined entities | **KEEP (core)** | One-sentence definitions for Harness, Agent Team, Skill, Orchestrator — the units AI cites. |
| Semantic / topical coverage | **KEEP** | Build the full "agent teams for Claude Code" topic cluster across README + docs. |
| Headings & lists for AI readability | **KEEP** | Tables and bullet lists (like this file) are highly extractable. |
| Relevant images, infographics, videos | **ADAPT** | Add a demo GIF/screencast (auditor R-item) — also improves human dwell time. |
| Clear CTAs | **ADAPT** | "Install via marketplace", "Star", "Read the quickstart." |
| FAQs when pertinent | **KEEP (high-value)** | Add an FAQ block (README + `FAQPage` schema on index.html) — directly feeds AI answer engines. |
| Align content to search intent | **KEEP** | Answer / guide / compare / transactional mapped to sections. |
| Encourage user-generated content | **ADAPT** | Showcase community harnesses, "Built with Harness" section, discussions. |
| Update content regularly | **KEEP** | Keep changelog + README fresh; freshness is an AI-trust signal. |
| Improve or remove thin pages | **KEEP** | Ensure each doc has substance; merge thin ones. |
| Optimize for voice search | **ADAPT** | Voice ≈ conversational AI queries — the question-headings + FAQ already cover this. |

---

## 5. Off-Page Authority

| Classic item | Disposition | Our-case action |
|--------------|-------------|-----------------|
| Build high-quality backlinks | **ADAPT** | Backlinks that matter: **awesome-lists** (awesome-claude-code, awesome-claude-skills), the Claude Code plugin marketplace, dev.to/blog write-ups. |
| Recover lost/broken links | **KEEP** | Monitor mentions; fix dead links pointing at the repo. |
| Monitor & replicate competitor links | **ADAPT** | See which awesome-lists list similar plugins; get Harness listed too. |
| Earn editorial links & brand mentions | **KEEP** | Newsletters (TLDR, Console.dev), YouTube devtool reviews, HN/Reddit organic. |
| Digital PR for mentions & authority | **ADAPT** | The Show HN + benchmark story is the PR hook. |
| Natural anchor text | **KEEP** | "Harness", "Harness Claude Code plugin" — branded + descriptive, not spammy. |
| Monitor backlink quality (disavow if needed) | **KEEP (light)** | Low risk for a repo; only watch for spam scrapers. |
| Promote in social & communities | **KEEP** | X/Twitter, LinkedIn, Claude/Discord, Reddit — per community-scout map. |
| Strengthen brand & online reputation | **KEEP** | Consistent naming, banner, tagline everywhere. |

> The community-scout outreach map (`_workspace/03_scout_outreach_map.md`) is the execution backbone for this domain — do not duplicate it; reference and prioritize it.

---

## 6. AI-Search (GEO/AEO) — ADDED for our case

Not present in the generic checklist, and the **single most important surface** for a developer tool discovered by asking an assistant. Full methodology in `ai-search-geo.md`. Summary levers:
- Allow AI crawlers in `robots.txt` (GPTBot, ClaudeBot, PerplexityBot, Google-Extended, CCBot).
- Add `llms.txt` at the Pages root pointing to the canonical docs.
- Make claims self-contained and quotable; define entities inline.
- Get cited in the sources AI models trust (GitHub, awesome-lists, docs sites).
- Track AI-referral traffic and test-prompt recommendations.

---

## 7. Marketplace/Registry SEO — REPLACES Local SEO

Classic "Local SEO" (Google Business Profile, NAP citations, maps, local reviews) is **N/A** for an open-source dev tool. Its authority-equivalent for us:

| Local-SEO concept | Our equivalent |
|-------------------|----------------|
| Google Business Profile | **Claude Code plugin marketplace listing** — complete, keyword-rich, with icon/banner. |
| Consistent NAP citations | **Consistent name/description/author** across `plugin.json`, `.claude-plugin/marketplace.json`, README, registries. |
| Local landing pages | Registry/marketplace detail page + Pages site. |
| Reviews & ratings | Stars, testimonials, "Built with Harness" evidence. |
| Local schema | `SoftwareApplication` schema (see §1). |
| Local directories | **MCP registries / awesome-lists / plugin directories.** |

---

## Disposition summary

- **KEEP (~as-is):** most Keyword, On-Page, Content, Off-Page items.
- **ADAPT (action changes):** all Technical items, entity mapping, titles/meta → repo About + index.html, backlinks → awesome-lists/marketplace.
- **ADD (new, repo/AI-specific):** GitHub Topics, repo About, AI-crawler access, `llms.txt`, FAQ+schema, demo GIF.
- **REPLACE:** Local SEO → Marketplace/Registry SEO.
- **N/A:** server-log monitoring, Google Business Profile / physical-local items.
