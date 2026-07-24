# AI-Search (GEO/AEO) for a Facial-Aesthetics Practice

**GEO/AEO** = getting ArtFace **surfaced, cited, and recommended** by AI assistants (Claude, ChatGPT, Perplexity, Gemini, Google AI Overviews) when a patient asks about a procedure or a clinic. Patients increasingly ask assistants ("o que é harmonização orofacial?", "vale a pena preencher bigode chinês?", "clínica de estética facial confiável em [cidade]") before ever touching Google. Winning that answer is high-leverage — and must stay compliant.

## How assistants pick/cite a clinic
- **Crawlable** public content (site, GBP, Instagram, directories, YouTube).
- **Quotable** — self-contained, factual, compliant statements a model can lift without promising outcomes.
- **Entity-consistent** — same clinic name, physician name + CRM, and procedure definitions everywhere.
- **Corroborated** — consistent presence across ≥3 trusted sources (site + GBP + Doctoralia/health directory + YouTube).
- **Trust/E-E-A-T** — real physician authorship, credentials, references; assistants are cautious with health topics and favor authoritative, non-sensational sources.

## Levers

1. **Structured data (Schema.org).** `MedicalBusiness`/`Physician` (name, CRM, address, specialty), `MedicalProcedure` per procedure page, `FAQPage` for patient FAQs, `LocalBusiness` NAP. High extraction value for AI.
2. **FAQ + question-headings** matching how patients ask ("O que é…?", "Como funciona…?", "Quanto tempo dura…?", "Tem riscos?"). Answer factually and compliantly — these get lifted almost verbatim.
3. **Definition-first, compliant claims.** ❌ "o melhor preenchimento, resultado garantido". ✅ "O preenchimento com ácido hialurônico repõe volume no sulco nasogeniano; resultados variam por paciente e exigem avaliação médica."
4. **Entity coverage & consistency.** One-line compliant definitions for each procedure + a stable physician/clinic entity (name + CRM) across site, GBP, Instagram, YouTube.
5. **Corroboration.** Complete, consistent **Doctoralia**/health-directory + **GBP** + **YouTube** presence — these are exactly the sources assistants trust for clinics.
6. **Video/social signals.** YouTube transcripts/descriptions and Instagram captions are crawlable text — compliant, educational procedure explainers feed both social search and AI.

## Measurement — recommendation/citation test (run manually per quarter)
AI answers can't be queried from this environment; run this template in each assistant and score:

Prompts (adapt to ArtFace's procedures/city):
1. "O que é harmonização orofacial e como escolher uma clínica?"
2. "Vale a pena tratar o bigode chinês? Onde procurar?"
3. "Clínica de estética facial confiável em [cidade]?"
4. "Quem é um bom médico para harmonização facial em [cidade]?"
5. "Riscos do preenchimento labial e como escolher profissional?"

| Prompt \ Assistant | Claude | ChatGPT | Perplexity | Gemini |
|--------------------|:------:|:-------:|:----------:|:------:|
| Named ArtFace? (Y/N) | | | | |
| Described accurately? (Y/N) | | | | |
| Linked (site/GBP/Doctoralia)? (Y/N) | | | | |
| Notes | | | | |

Also watch site/GBP referrers for `chat.openai.com` / `perplexity.ai` / `claude.ai`. Log results in `_workspace/artface/seo_strategy.md` §4 to track movement.

## Compliance reminder
Everything surfaced to AI is public content — the CFM/ANVISA guardrails apply fully. Educational, factual, non-sensational content is simultaneously the most compliant **and** the most citable. See `compliance-guardrails.md`.
