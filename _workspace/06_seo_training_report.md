# SEO Strategist — Training & Validation Report

**Date:** 2026-07-24
**Scope:** New `seo-strategist` agent + `seo-strategy` skill (adapted from an external "AI-ready SEO checklist").
**Method:** Harness Phase 6 — structure check, trigger validation, and a live execution ("training") run.

---

## 1. What was built

| Artifact | Path | Purpose |
|----------|------|---------|
| Agent (responsible) | `.claude/agents/seo-strategist.md` | The specialist that owns SEO/AI-discoverability, integrated with the launch team. |
| Skill (the "training"/knowledge) | `.claude/skills/seo-strategy/SKILL.md` | The AI-ready checklist adapted to our case; 7-domain scored workflow. |
| Reference — full checklist | `.claude/skills/seo-strategy/references/checklist-full.md` | Every classic item mapped: KEEP / ADAPT / REPLACE / N/A. |
| Reference — GEO/AEO | `.claude/skills/seo-strategy/references/ai-search-geo.md` | The AI-search discipline (new to our case). |
| Harness pointer | `CLAUDE.md` | Trigger rules + change log. |
| Strategy output | `_workspace/05_seo_strategy.md` | The live run's scored strategy for the repo. |

**Adaptation summary (image → our case):** the source checklist targets a marketing website. It was translated to an open-source Claude Code plugin: Search Console → GitHub Insights + GSC for the Pages site; on-page titles → repo About + GitHub Topics + `index.html` meta; backlinks → awesome-lists + marketplace/registries; **Local SEO → Marketplace/Registry SEO (replaced)**; and a **new domain 6, AI-Search (GEO/AEO)**, was added because that is the decisive surface for a dev tool and is absent from the generic checklist.

---

## 2. Structure validation (Phase 6-1)

- [x] Agent file at `.claude/agents/seo-strategist.md` with all required sections (role, principles, I/O protocol, team-comms, error handling, collaboration).
- [x] `model: opus` set on the agent.
- [x] Skill frontmatter has `name` + `description`; description is pushy and includes follow-up keywords ("atualiza a estratégia", "re-roda o SEO").
- [x] SKILL.md body under 500 lines; exhaustive detail moved to `references/`.
- [x] No commands created under `.claude/commands/`.
- [x] No duplication: complements `repo-auditor` (owns discoverability *in depth*), feeds `content-creator` and `launch-strategist` rather than overlapping.

---

## 3. Trigger validation (Phase 6-4)

### Should-trigger (the skill must fire)
| # | Query | Fires? |
|---|-------|:------:|
| 1 | "Verifica se já temos essa estratégia de SEO e melhora pro nosso caso" | ✅ |
| 2 | "Como deixar o Harness mais fácil de achar no Google e no GitHub?" | ✅ |
| 3 | "A gente precisa aparecer quando perguntam pro ChatGPT sobre plugins do Claude Code" (AI-search) | ✅ |
| 4 | "Faz um checklist de SEO pro repositório" | ✅ |
| 5 | "Quais GitHub Topics e social preview devo configurar?" | ✅ |
| 6 | "Otimiza o index.html pra busca por IA / GEO / AEO" | ✅ |
| 7 | "Atualiza a estratégia de SEO que a gente rodou" (follow-up) | ✅ |
| 8 | "Como conseguir backlinks e entrar nas awesome-lists?" | ✅ |
| 9 | "Pesquisa de palavras-chave pro nosso público de devs" | ✅ |

### Should-NOT-trigger (near-misses — a different agent/skill owns it)
| # | Query | Correct owner | Fires? |
|---|-------|---------------|:------:|
| 1 | "Cria um harness de agentes pra um novo projeto de dados" | `harness` meta-skill | ❌ |
| 2 | "Escreve o post do Show HN do lançamento" | `content-creator` (SEO only *feeds* it) | ❌ |
| 3 | "Faz a auditoria geral do repo pra trending" | `repo-auditor` | ❌ |
| 4 | "Monta o cronograma de lançamento" | `launch-strategist` | ❌ |
| 5 | "Submete o PR nas awesome-lists" (execution) | `community-scout` (strategy vs execution) | ❌ |
| 6 | "Refatora o JavaScript do index.html" | code quality, not discoverability | ❌ |
| 7 | "Traduz o README pro espanhol" | i18n/content | ❌ |
| 8 | "Adiciona testes de CI ao repo" | repo hygiene | ❌ |

**Boundary note:** off-page (backlinks/outreach) and content overlap with `community-scout` and `content-creator`. The clean line: **`seo-strategy` owns the strategy/scoring/prescription; the other agents own execution** (writing copy, submitting PRs). The near-misses above confirm the boundary holds.

---

## 4. Execution ("training") run

An independent agent embodied `seo-strategist`, loaded the agent definition + skill, and ran the full workflow against the real repo — validating that agent + skill work end-to-end when invoked fresh. Output: `_workspace/05_seo_strategy.md`.

**Result — 50 material items scored:**
| State | Count |
|-------|:-----:|
| Have | 10 |
| Partial | 17 |
| Missing | 19 |
| Unknown (verify in UI) | 2 |
| N/A | 2 |

**Verdict produced:** we do **not** have a dedicated AI-ready SEO strategy; prior coverage was only repo-auditor's partial "Discoverability (7/10)". Baseline now established across all 7 domains.

**Top 5 prioritized actions:** (1) set GitHub Topics, (2) set repo About + website, (3) `index.html` meta description + canonical, (4) Schema.org JSON-LD (`SoftwareApplication` + `FAQPage`), (5) `robots.txt` allowing AI crawlers — all High-impact / Low-effort.

**High-value catch:** the run detected a real entity/naming inconsistency — "Team-Architecture Factory" (README/plugin.json) vs "Agent Team & Skill Architect" (index.html) — which fragments the entity for LLMs. Flagged as a High/Low GEO fix (G5).

## 5. Feedback loop — skill improvements applied (Phase 6 iterative refinement)

The run surfaced 5 friction points; the generalizable ones were folded back into the skill (not overfit to this repo):

| # | Feedback | Fix applied |
|---|----------|-------------|
| 1 | Pages-site items assumed a live Pages deployment that isn't confirmed | Added a **Pages-dependency gate** to SKILL.md Step 1 + checklist header: Pages-hosted items can't be scored "Have" until deployment is verified. |
| 2 | State legend differed across the 3 files ("N/A" vs "Unknown") | **Standardized one 5-state legend** (Have / Partial / Missing / Unknown-verify-in-UI / N/A) across SKILL.md, checklist-full.md, and the agent definition. |
| 3 | "Items per domain" vs flat-table schema was ambiguous | Clarified the schema table is **grouped by domain**. |
| 4 | Entity/naming-consistency check had no home in the workflow (was a lucky catch) | Added **Step 1.5 — Diff the product identity across surfaces**, making the naming-consistency diff a deliberate, guaranteed step. |
| 5 | Owner-agent roster omitted community-scout | **Listed the full owner roster** (incl. community-scout for off-page) in Step 4. |

**Conclusion:** the agent + skill are coherent and runnable end-to-end; trigger boundaries hold; the first live run produced a grounded, prioritized strategy and improved the skill through the feedback loop. The `seo-strategist` is trained and operational.
