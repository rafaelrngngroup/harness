# CLAUDE.md — Harness project harness pointer

This repo ships the **Harness** plugin (a meta-skill for building agent teams, under `skills/harness/`) and also runs its **own** launch/discoverability harness for taking the project to market. Outputs of launch runs live in `_workspace/`.

## Harness: Launch & Discoverability

**Goal:** Make Harness maximally findable and recommendable on GitHub, classic web search, and AI assistants — and drive an effective open-source launch.

**Triggers:**
- SEO / discoverability / "descoberta" / ranking / "busca por IA" / GEO / AEO / keywords / backlinks / GitHub Topics / social preview / "checklist de SEO" → use the **`seo-strategy`** skill (`.claude/skills/seo-strategy/`), owned by the **`seo-strategist`** agent (`.claude/agents/seo-strategist.md`). It scores a 7-domain checklist adapted to our case and writes `_workspace/05_seo_strategy.md`.
- Launch / audit / outreach / content requests build on the launch team artifacts already in `_workspace/` (repo-auditor, content-creator, community-scout, launch-strategist).

Simple questions can be answered directly without invoking the harness.

**Change log:**
| Date | Change | Target | Reason |
|------|--------|--------|--------|
| 2026-07-24 | Added SEO & AI-discoverability agent + skill; ran initial strategy | `.claude/agents/seo-strategist.md`, `.claude/skills/seo-strategy/`, `_workspace/05_seo_strategy.md` | Adopt & adapt an AI-ready SEO checklist for our case (GitHub + web + AI-search); prior coverage was only the auditor's partial "Discoverability" scoring |
