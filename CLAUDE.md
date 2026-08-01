# CLAUDE.md — Harness project harness pointer

This repo ships the **Harness** plugin (a meta-skill for building agent teams, under `skills/harness/`) and also runs its **own** launch/discoverability harness for taking the project to market. Outputs of launch runs live in `_workspace/`.

## Harness: Launch & Discoverability

**Goal:** Make Harness maximally findable and recommendable on GitHub, classic web search, and AI assistants — and drive an effective open-source launch.

**Triggers:**
- SEO / discoverability / "descoberta" / ranking / "busca por IA" / GEO / AEO / keywords / backlinks / GitHub Topics / social preview / "checklist de SEO" → use the **`seo-strategy`** skill (`.claude/skills/seo-strategy/`), owned by the **`seo-strategist`** agent (`.claude/agents/seo-strategist.md`). It scores a 7-domain checklist adapted to our case and writes `_workspace/05_seo_strategy.md`.
- Launch / audit / outreach / content requests build on the launch team artifacts already in `_workspace/` (repo-auditor, content-creator, community-scout, launch-strategist).

Simple questions can be answered directly without invoking the harness.

## ArtFace: Discoverability (private tooling → public marketing)

**Goal:** Make **ArtFace's public properties** (clinic site, landing pages, Instagram, YouTube, Google Business Profile) findable by patients on Google, Maps/local, social, and AI assistants — while the code/tooling here stays private.

**Triggers:**
- SEO/descoberta da ArtFace, "aparecer no Google", "Google Meu Negócio / SEO local", palavras-chave de procedimento, "busca por IA" / GEO / AEO, Instagram/YouTube SEO, otimizar protocolo/campanha para busca → use the **`artface-seo`** skill (`.claude/skills/artface-seo/`), owned by the **`artface-seo-strategist`** agent (`.claude/agents/artface-seo-strategist.md`). Local SEO is central; every content item passes CFO/ANVISA (dental-advertising) compliance guardrails. Pairs with `artface-protocol-builder`.

**Privacy note (DEFERRED by owner, 2026-07-24):** this repo is a *fork* of a public repo, so it is public and cannot simply be flipped to private. Owner's decision: **keep the code open for now** and do the **full migration to a private (non-fork) repository as the final step**, once the ArtFace engine is complete and running. Do not spend time closing the code before then — but keep this as the last checklist item.

**Change log:**
| Date | Change | Target | Reason |
|------|--------|--------|--------|
| 2026-07-24 | Added SEO & AI-discoverability agent + skill; ran initial strategy | `.claude/agents/seo-strategist.md`, `.claude/skills/seo-strategy/`, `_workspace/05_seo_strategy.md` | Adopt & adapt an AI-ready SEO checklist for our case (GitHub + web + AI-search); prior coverage was only the auditor's partial "Discoverability" scoring |
| 2026-07-24 | Executed top technical SEO actions | `index.html` (meta/canonical/OG/Twitter/Schema.org), `robots.txt`, `llms.txt`, `sitemap.xml` | Ship the High-impact/Low-effort file-based wins the seo-strategist owns (G1–G3 + on-page) |
| 2026-07-24 | Ran G8 AI-search baseline | `_workspace/07_g8_ai_search_baseline.md` | Establish the "before" visibility measurement (3/10 queries; all equity upstream, fork invisible) |
| 2026-07-24 | **Scope → private/internal (ArtFace-only)** | `_workspace/05` §5, this log | Owner clarified the fork is private, exclusive to ArtFace; public discoverability cancelled, public-facing SEO files kept dormant, agent+skill retained as internal tooling (re-aimable at ArtFace's own presence) |
| 2026-07-24 | Re-aimed SEO at ArtFace's public presence | `.claude/agents/artface-seo-strategist.md`, `.claude/skills/artface-seo/` | Build the discoverability tool for ArtFace's real target (clinic site/Instagram/YouTube/Google Business Profile), Local-SEO-central, compliance baked in; pairs with artface-protocol-builder |
| 2026-07-24 | Ran live ArtFace strategy + **CFM→CFO correction** | `_workspace/artface/seo_strategy.md`, `.claude/skills/artface-seo/`, `.claude/agents/artface-seo-strategist.md` | Owner-confirmed the professional is a **cirurgião-dentista (CRO-SC 18.965), not médico** (CNPJ 34.097.019/0001-10, CNAE 86.30-5-04 odontologia). Corrected compliance basis CFM→CFO across skill+agent; before/after now permitted per Res. CFO-196/2019; schema `Physician`→`Dentist` |
