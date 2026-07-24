---
name: artface-seo
description: "SEO & AI-discoverability strategy for ArtFace — a facial-aesthetics practice (harmonização orofacial, estética/cirurgia facial). Makes ArtFace's PUBLIC properties (clinic site, landing pages, Instagram, YouTube, Google Business Profile) findable by patients on Google, Maps/local, social, and AI assistants — with Brazilian medical-advertising compliance (CFM/ANVISA) baked in. Use whenever the task is about making ArtFace findable/rankable: 'SEO da ArtFace', 'aparecer no Google', 'Google Meu Negócio / SEO local', 'palavras-chave de procedimento', 'busca por IA / GEO / AEO', 'Instagram/YouTube SEO', 'landing page achável', 'otimizar protocolo/campanha para busca'. Pairs with artface-protocol-builder so every protocol and campaign ships search-ready and compliant. NOT for optimizing open-source code/repos."
---

# ArtFace SEO — Findable Aesthetics Practice (Compliant by Design)

Make ArtFace's **public** content findable by the patients it wants — on **Google** (organic + Maps/local), **Instagram & YouTube**, and **AI assistants** — while keeping the practice's tooling and methods private. Unlike a generic web-SEO checklist, this is tuned to a **facial-aesthetics clinic**: **Local SEO is central**, patient-vs-clinical language must both be owned, and **medical-advertising compliance (CFM/ANVISA) is a hard constraint**, never an afterthought.

## When to use
- Any request to make ArtFace more findable on Google, Maps, Instagram, YouTube, or AI assistants.
- Optimizing a landing page, procedure page, protocol, or campaign for search (pairs with `artface-protocol-builder`).
- Setting up / improving the Google Business Profile and local presence.
- Re-running/updating a prior `_workspace/artface/seo_strategy.md`.

## Compliance first — read before proposing any public content
Brazilian medical-advertising norms (CFM, ANVISA) constrain what a physician may publish. Treat these as **hard guardrails**; when a specific rule is uncertain, flag it for the practice's compliance/legal review rather than asserting a citation.

- **No sensationalism or guaranteed results.** Avoid "melhor", "resultado garantido", "sem riscos", superlatives, and promises. Describe procedures factually.
- **Before/after imagery is restricted.** Do not use before/after as promotional bait; if used at all, only within the contexts and disclaimers the norms allow. Default to education over transformation showcases.
- **No price/discount sensationalism**, no promotions that trivialize procedures, no "self-esteem pressure" framing.
- **Show real E-E-A-T:** physician name, CRM/RQE where applicable, credentials, references. Never fabricate credentials or outcomes.
- **Educational, patient-first framing wins** — it is both compliant and what LLMs/patients reward.

> Every content recommendation this skill emits carries a one-line compliance note. If a high-reach tactic conflicts with the guardrails, replace it with the compliant alternative and say why. Full guidance: `references/compliance-guardrails.md`.

## The domains (scored)

Score each item **Have / Partial / Missing / Unknown-provide-to-run / N/A(reason)**; each recommendation carries **surface** (Google / Local / Social / AI-search), **impact**, **effort**, and a **compliance note**.

| # | Domain | Center of gravity for ArtFace |
|---|--------|-------------------------------|
| 1 | **Local SEO (central)** | Google Business Profile, NAP consistency, categories/services, reviews, Maps, per-city/per-procedure local pages. Detail: `references/local-seo-playbook.md` |
| 2 | **On-Page & Technical** | Titles/meta/H1, Schema.org (`MedicalBusiness`/`Physician`/`MedicalProcedure`/`FAQPage`), canonical, Core Web Vitals, mobile-first |
| 3 | **Keyword & Entity** | Lay ↔ clinical mapping (bigode chinês ↔ sulco nasogeniano), "near me" intent, procedure entities. Detail: `references/procedure-keyword-map.md` |
| 4 | **Content (human + LLM), compliant** | Patient-question content, E-E-A-T, FAQ, question-headings, quotable + compliant |
| 5 | **Social & Video SEO** | Instagram (bio/alt/captions/hashtags/geotag/Reels) + YouTube (titles/desc/chapters/transcripts) |
| 6 | **AI-Search (GEO/AEO)** | Surfacing in assistant answers for procedure + local queries. Detail: `references/geo-aeo-aesthetics.md` |

## Workflow

### Step 0 — Context & properties
Gather ArtFace's live properties: site URL, landing pages, Instagram/YouTube handles, Google Business Profile, **target city/region**, and **priority procedures**. Anything missing → mark **Unknown-provide-to-run** (never invent URLs, addresses, phone, or metrics). Read any prior `_workspace/artface/seo_strategy.md` and improve deltas.

### Step 1 — Local SEO audit (do this first)
For a clinic, local signals usually outrank generic organic. Walk `references/local-seo-playbook.md`: Google Business Profile completeness, NAP consistency across site/Instagram/directories, categories/services, photos, review flow, and per-city/per-procedure local pages.

### Step 2 — Keyword & entity map (lay ↔ clinical)
Build the procedure map from `references/procedure-keyword-map.md`: for each priority procedure, the lay term patients type, the clinical term, "near me"/transactional variants, and the owning page. Map intent.

### Step 3 — On-page, technical & content
Score titles/meta/schema/CWV; specify the content plan (procedure pages, FAQ blocks, question-headings) — each item passing the compliance guardrail.

### Step 4 — Social, video & AI-search
Instagram/YouTube optimization + the GEO/AEO layer (`references/geo-aeo-aesthetics.md`): quotable compliant claims, entity coverage, corroboration, and a recommendation/citation test template for the 4 assistants.

### Step 5 — Prioritize & emit
Rank Missing/Partial items by impact × (1/effort); front-load High/Low (Google Business Profile completion, NAP fixes, procedure-page titles/schema, FAQ). Write `_workspace/artface/seo_strategy.md` using the output schema below.

## Output schema — `_workspace/artface/seo_strategy.md`

```markdown
# ArtFace — SEO & AI-Discoverability Strategy
**Date:** {YYYY-MM-DD} · **City/region:** {…} · **Priority procedures:** {…}
**Compliance basis:** CFM/ANVISA medical-advertising guardrails (see skill)

## 0. Properties & scope (what's live / Unknown-provide-to-run)

## 1. Scored checklist (6 domains)
| Domain | Item | State | Surface | Impact | Effort | Compliance note |

## 2. Keyword & entity map (lay ↔ clinical, per procedure)

## 3. Local SEO plan (Google Business Profile, NAP, reviews, local pages)

## 4. AI-search (GEO/AEO) plan + 4-assistant recommendation-test template

## 5. Prioritized actions (impact × effort) + owner

## 6. Compliance flags (anything to route to legal/compliance)
```

## Guardrails
- **Compliance beats reach.** Never ship a non-compliant tactic for visibility; offer the compliant alternative.
- **Local before generic.** For a clinic, Maps/reviews/"near me" usually beat broad organic — prioritize accordingly.
- **Own both languages.** Lay term for discovery, clinical term for authority; link them on-page.
- **Proof, not adjectives.** Real credentials/authorship; never fabricate outcomes or superlatives.
- **Findable, not exposed.** Optimize public marketing; never recommend publishing private protocols, pricing logic, or proprietary methods for reach.
- **Stay lean.** This SKILL.md is the map; playbooks live in `references/` and load only when needed.

## References
- `references/local-seo-playbook.md` — Google Business Profile, NAP, reviews, Maps, local pages (the central domain).
- `references/procedure-keyword-map.md` — lay↔clinical keyword/entity map across common facial procedures + intent.
- `references/geo-aeo-aesthetics.md` — AI-search for aesthetics: quotable compliant content, entity coverage, corroboration, 4-assistant test.
- `references/compliance-guardrails.md` — CFM/ANVISA advertising guardrails, principle-based, with a "route to legal" checklist.
