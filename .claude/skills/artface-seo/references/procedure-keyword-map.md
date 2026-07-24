# Procedure Keyword & Entity Map — Lay ↔ Clinical

Patients search in **lay language**; authority and AI-entity reasoning live in **clinical language**. ArtFace must own **both** and link them on-page. This is a starter map — extend per ArtFace's priority procedures and confirm clinical terms with the dentist.

## How to use
For each priority procedure, fill: lay term(s) patients type · clinical term · common "near me"/intent variants · owning page. Map intent: **informational** ("o que é / como funciona"), **navigational** (brand), **transactional/local** ("preço", "perto de mim", "[cidade]", "agendar").

## Starter map (facial aesthetics)

| Lay term (patient) | Clinical term | Intent variants | Owning page |
|--------------------|---------------|-----------------|-------------|
| bigode chinês | sulco nasogeniano | "preencher bigode chinês", "…em [cidade]" | página do procedimento |
| olheira | hiperpigmentação / hérnia de gordura periorbital | "tratamento de olheira", "olheira preenchimento" | procedimento periorbital |
| papada | gordura submentoniana | "tratar papada sem cirurgia", "…perto de mim" | procedimento submentoniano |
| bochecha caída / flacidez | ptose de terço médio / flacidez facial | "lifting sem cirurgia", "fios de sustentação" | flacidez / fios PDO |
| pé de galinha / rugas | rugas dinâmicas periorbitais | "botox pé de galinha", "toxina botulínica" | toxina botulínica |
| harmonização facial | harmonização orofacial (HOF) | "harmonização facial [cidade]", "quanto custa" | pilar / hub HOF |
| preenchimento labial | preenchimento de lábios (ácido hialurônico) | "preenchimento labial natural" | procedimento labial |
| queixo / mento | projeção de mento | "preenchimento de queixo" | mento |
| flacidez de pele | bioestimulador de colágeno | "bioestimulador", "colágeno" | bioestimuladores |
| mancha / melasma | melasma / hipercromia | "tratamento de melasma", "…em [cidade]" | melasma |
| ptose palpebral | ptose palpebral | "correção de ptose", "blefaroplastia" | blefaro / ptose |

## Entities (for LLM reasoning)
Give each a crawlable, compliant one-line definition, used consistently across site + social:

- **Harmonização orofacial (HOF)** — especialidade odontológica (Res. CFO-198/2019) que reúne procedimentos para equilíbrio estético e funcional da face, individualizado por avaliação clínica.
- **Ácido hialurônico / bioestimulador / toxina botulínica** — factual descriptions (mechanism, indication) without promises.
- **ArtFace** — the practice/brand + dentist (name, CRO).
- **Dr. Rafael** — dentist entity (credentials, CRO) — the E-E-A-T anchor.

## Rules
- **Lay term for discovery, clinical for authority** — put the lay term in headings/FAQ ("O que é bigode chinês?") and the clinical term in the body/definition.
- **Intent → page**: informational to procedure/education pages; local/transactional to local landing pages + GBP.
- **Compliant naming only** — no "melhor", "definitivo", "sem risco" in titles or keywords.
- Prioritize **low-competition, high-intent local long-tails** ("[procedimento] em [cidade]") over broad head terms.
