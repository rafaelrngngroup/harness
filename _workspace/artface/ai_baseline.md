# ArtFace — AI-Search / Recommendation BASELINE ("before" measurement)

**As of:** 2026-07-24
**Method:** Classic web-search visibility (WebSearch) as a proxy for AI-answer inputs + a manual assistant-recommendation template. See `references/geo-aeo-aesthetics.md`.
**Honesty note:** This environment CANNOT query ChatGPT/Perplexity/Gemini/Claude directly. STEP 1–2 below are real web-search observations (an input AI models reason over). STEP 3 is a template to run by hand. WebSearch returns the organic list only — it does **not** render Google's Maps/local pack, so GBP presence is marked *Unknown — manual check required*, never asserted.

## Grounding facts (source: task brief + confirmed in results)
- Brand: **ArtFace® Harmonização Facial** · site **clinicaartface.com.br** · IG **@artface.bc** · Doctoralia profile live.
- Dr. **Rafael Lucci (dos Santos)**, **cirurgião-dentista** (NOT médico). CRO-SC 18.965 (task) — web results also list **CRO-PR 17.398** (source: Doctoralia).
- City: **Balneário Camboriú/SC**. Address surfacing in results: Rua 1300, nº 25, Centro, CEP 88330-549 (source: search snippets — verify NAP against GBP).

---

## STEP 1 — Classic web-search visibility (proxy)

Legend: position = rough rank within the organic result list returned (not Google's live SERP; the local pack is not visible here).

| # | Query (patient language) | ArtFace appears? | Rough pos. | Property surfaced | Competitors ranking above (named) |
|---|--------------------------|:----------------:|:----------:|-------------------|-----------------------------------|
| 1 | harmonização facial Balneário Camboriú | **Yes** | ~6 / 9 | Homepage (clinicaartface.com.br) | Dr. Viotto (drviotto.com.br), CEO Clínica, Vizzari, Dra. Caroline Morgental, Unique Odontologia |
| 2 | harmonização orofacial Balneário Camboriú | **Yes** | ~6 / 10 | Homepage | Dra. Rosalia Grassi, Dra. Aletéya, Rede IOA (curso), Unique Odontologia, Dra. Caroline Morgental |
| 3 | bigode chinês preenchimento Balneário Camboriú | **No** | — | — | Dra. Rosalia Grassi, **Doctoralia** (agregador), Clínica Marina Ceruti, Unique Odontologia |
| 4 | botox Balneário Camboriú | **No** | — | — | **Doctoralia**, Botoclinic Balneário Shopping, Dr. Gabriel Brognoli, Clínica Biavatti, Clínica Inovate |
| 5 | harmonização de mandíbula / jawline Balneário Camboriú | **Yes** | ~2 / 9 | **/protocolos** page (pos ~2) + homepage (~6) | CEO Clínica (#1) |
| 6 | tratamento de olheiras Balneário Camboriú | **Yes** | ~7 / 9 | Homepage | **Doctoralia**, Oftalmos (oftalmologia — baixa relevância), Dra. Caroline Morgental |
| 7 | melhor clínica de harmonização facial Balneário Camboriú | **Yes** | ~3 / 8 | Homepage | Dr. Viotto (#1 e #2, dois resultados) |
| 8 | ArtFace harmonização facial (brand) | **Yes** | #1 | IG @artface.bc (#1), Facebook (#2), ReclameAqui (#3), site (#4) | — (brand-owned, but ReclameAqui e IG rankeiam acima do site próprio) |

**Reading of STEP 1:**
- ArtFace surfaces on **6 / 8** queries — strong on generic "harmonização (oro)facial" and brand, and notably **#2 on jawline via the /protocolos page** (the only procedure-level page ranking well).
- **Two high-intent transactional gaps: "botox" and "bigode chinês"** — the exact lay terms with buying intent — return **zero** ArtFace properties; **Doctoralia intercepts** both.
- On olheiras, the competition is mostly ophthalmology clinics (low relevance) — an easy win with a dedicated page.
- On brand queries, **ReclameAqui ranks above the clinic's own site** — a reputation-surface risk to monitor.

---

## STEP 2 — Corroboration & properties check

**Independent / trusted sources currently mentioning ArtFace** (source-tagged):

| Source | Type | Independent 3rd-party? | Note |
|--------|------|:----------------------:|------|
| clinicaartface.com.br (+ /protocolos) | Own site | No (first-party) | Ranks broadly; /protocolos is the strongest procedure page |
| Instagram @artface.bc | Own social | No (first-party) | ~20K followers (source: snippet) |
| Facebook /artface.bc | Own social | No (first-party) | Live |
| **Doctoralia** (Rafael Lucci dos Santos) | Health directory | **Yes** | Live profile; CRO-PR + CRO-SC listed — the single most AI-trusted corroborator for a clinic |
| **ReclameAqui** (ArtFace BC Odontologia) | Reputation | **Yes** | Live; carries complaints — monitor |
| **ZoomInfo** (ArtFace) | Business directory | **Yes** | Company listing |

**Independent trusted sources = 3** (Doctoralia, ReclameAqui, ZoomInfo), plus 3 first-party properties. The GEO/AEO bar is "consistent presence across ≥3 trusted sources" — ArtFace **meets the count**, but the mix is thin: only **one health-authority corroborator (Doctoralia)** and **no confirmed GBP**. YouTube: **not observed** in any result (likely Missing).

**GBP / Google Maps surfacing:** **Unknown — manual check required.** No maps.google.com / local-pack result appeared in the organic text for the local queries. WebSearch does not render Google's local pack, so this is **not** evidence of absence — it must be verified by a manual "harmonização facial Balneário Camboriú" search on Google + a `google.com/maps` lookup for the clinic name/address. Confirming and completing the GBP is the highest-leverage local action.

---

## STEP 3 — Generative-assistant recommendation test TEMPLATE (NOT executed)

Run once per quarter, manually, in each assistant. Do not fabricate — fill only with observed answers. Watch site/GBP referrers for `chat.openai.com`, `perplexity.ai`, `claude.ai`, `gemini.google.com`.

**Rubric per cell:** Named ArtFace? (Y/N) · Described accurately as **dentist + HOF + CRO-SC 18.965** (not médico)? (Y/N) · Linked (site/GBP/Doctoralia)? (Y/N) · Notes.

**Prompt 1 — "O que é harmonização orofacial e como escolher uma clínica em Balneário Camboriú?"**

| | Claude | ChatGPT | Perplexity | Gemini |
|---|:--:|:--:|:--:|:--:|
| Named ArtFace? | | | | |
| Described accurately (dentista+HOF+CRO)? | | | | |
| Linked (site/GBP/Doctoralia)? | | | | |
| Notes | | | | |

**Prompt 2 — "Vale a pena tratar o bigode chinês? Onde procurar em Balneário Camboriú?"**

| | Claude | ChatGPT | Perplexity | Gemini |
|---|:--:|:--:|:--:|:--:|
| Named ArtFace? | | | | |
| Described accurately (dentista+HOF+CRO)? | | | | |
| Linked (site/GBP/Doctoralia)? | | | | |
| Notes | | | | |

**Prompt 3 — "Clínica de harmonização/estética facial confiável em Balneário Camboriú?"**

| | Claude | ChatGPT | Perplexity | Gemini |
|---|:--:|:--:|:--:|:--:|
| Named ArtFace? | | | | |
| Described accurately (dentista+HOF+CRO)? | | | | |
| Linked (site/GBP/Doctoralia)? | | | | |
| Notes | | | | |

**Prompt 4 — "Quem é um bom profissional para harmonização facial masculina em Balneário Camboriú?"**

| | Claude | ChatGPT | Perplexite | Gemini |
|---|:--:|:--:|:--:|:--:|
| Named ArtFace? | | | | |
| Described accurately (dentista+HOF+CRO)? | | | | |
| Linked (site/GBP/Doctoralia)? | | | | |
| Notes | | | | |

**Prompt 5 — "Riscos do preenchimento labial e como escolher um profissional?"**

| | Claude | ChatGPT | Perplexity | Gemini |
|---|:--:|:--:|:--:|:--:|
| Named ArtFace? | | | | |
| Described accurately (dentista+HOF+CRO)? | | | | |
| Linked (site/GBP/Doctoralia)? | | | | |
| Notes | | | | |

**Scoring:** count Y across 5 prompts × 4 assistants = /20 per rubric row. Baseline expectation given STEP 1–2 (proxy, not measured): **low** — ArtFace is invisible on transactional procedure queries and has only one strong health-directory corroborator, the two signals assistants lean on most.

---

## STEP 4 — Baseline scorecard — AS OF 2026-07-24

| Metric | Value (source: STEP 1–2 web search, 2026-07-24) |
|--------|--------|
| Queries where ArtFace appears / total | **6 / 8** |
| High-intent transactional queries covered | **0 / 2** ("botox", "bigode chinês" — both absent) |
| Best position (non-brand) | **~#2** — /protocolos page on "jawline / mandíbula" |
| Best position (brand) | **#1** — IG @artface.bc |
| Properties that surface | Own site + **/protocolos** page, Instagram, Facebook, Doctoralia, ReclameAqui, ZoomInfo |
| GBP / Maps surfacing | **Unknown — manual check required** (local pack not visible via WebSearch; not observed in organic text) |
| Independent corroborating sources | **3** (Doctoralia, ReclameAqui, ZoomInfo); YouTube not observed |
| Top 3 local competitors | 1) **Dr. Viotto** (domina genérico + "melhor clínica", 2 resultados) · 2) **CEO Clínica** (#1 em jawline, forte no genérico) · 3) **Unique Odontologia** (amplo em orofacial/preenchimento). Recorrentes: Dra. Caroline Morgental, Dra. Jucielle Quintana, Dra. Rosalia Grassi. Em transacional ("botox"/"bigode chinês"), **Doctoralia** é o concorrente estrutural. |
| **Single biggest visibility gap** | **No procedure-level pages ranking for transactional lay terms** ("botox [cidade]", "bigode chinês [cidade]") — Doctoralia intercepts that high-intent demand — **compounded by an unconfirmed/likely-incomplete Google Business Profile.** The /protocolos jawline result proves procedure pages CAN rank; the fix is per-procedure local landing pages + a complete GBP surfacing in the local pack. |

**Compliance note (applies to every follow-up action):** the fix is *educational, factual, per-procedure pages* (definition-first, lay↔clinical term, FAQ, `MedicalProcedure`/`FAQPage` schema, real authorship w/ CRO-SC 18.965) — which is simultaneously the most CFO/ANVISA-compliant and the most AI-citable format. No before/after as bait, no guaranteed results, no sensationalism. See `compliance-guardrails.md`.

**Next re-measure:** re-run STEP 1 (same 8 queries) + STEP 3 (manual, 4 assistants) quarterly; log deltas here and in `seo_strategy.md` §4.
