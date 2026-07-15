---
name: voice-creative
description: "Gera criativos de áudio com a voz clonada do proprietário (via Voicebox) para envio a pacientes e leads. Usar quando: (1) 'gera um áudio com a minha voz', 'criativo de voz', 'áudio para paciente/lead', (2) explicar a consulta automatizada por áudio, (3) criar mensagens de voz para campanhas, follow-up, lembretes ou boas-vindas, (4) configurar/verificar a integração com o Voicebox (clonagem de voz, API, MCP)."
---

# Voice Creative — Criativos de Áudio com Voz Clonada

Skill para gerar áudios com a voz clonada do proprietário usando o [Voicebox](https://github.com/jamiepine/voicebox) (estúdio de voz local, open-source, MIT), destinados a pacientes e leads — por exemplo, explicando como funciona uma consulta feita pela automação da clínica.

**Princípios:**

1. **Somente a própria voz, com consentimento.** Esta skill clona exclusivamente a voz do proprietário da conta, a partir de amostra gravada por ele. Nunca clonar voz de terceiros.
2. **Transparência com o destinatário.** Mensagens automatizadas devem se identificar como parte da automação da clínica (ver templates). Isso protege a confiança do paciente e atende à LGPD.
3. **Local-first.** O Voicebox roda localmente (ou via Docker) — a amostra de voz e os áudios gerados não saem da infraestrutura do proprietário.
4. **Roteiro antes de áudio.** Todo áudio nasce de um roteiro escrito, revisado e aprovado. O texto é o artefato versionável; o áudio é o produto final.

## Pré-requisitos

Antes da primeira geração, o ambiente precisa estar preparado (uma única vez):

1. Voicebox instalado e rodando — ver `references/voicebox-setup.md`
2. Perfil de voz do proprietário criado a partir de amostra de referência (clonagem zero-shot) — ver `references/voicebox-setup.md` §3
3. `profile_id` do perfil anotado (obtido via `GET /profiles`)
4. Engine com suporte a português selecionada — **Chatterbox Multilingual** (23 idiomas, incluindo `pt`)

Se algum pré-requisito faltar quando a skill for acionada, orientar o usuário pelo setup antes de tentar gerar áudio.

## Workflow

### Fase 1: Briefing do criativo

Identificar no pedido do usuário:

- **Público**: paciente (já em atendimento) ou lead (prospecto)
- **Objetivo**: explicar a consulta automatizada, boas-vindas, lembrete, follow-up, campanha
- **Canal**: WhatsApp, e-mail com áudio anexo, etc. (afeta duração-alvo)
- **Duração-alvo**: WhatsApp ideal 30–60s (~80–150 palavras); máx. recomendado 90s

Se o objetivo corresponder a um template existente, partir dele (`references/script-templates.md`).

### Fase 2: Roteiro

1. Escrever o roteiro em pt-BR, tom falado e natural (frases curtas, sem siglas não explicadas)
2. Incluir a identificação de automação quando o áudio for disparado automaticamente
3. Apresentar o roteiro ao usuário para aprovação **antes** de gerar o áudio
4. Salvar roteiros aprovados para reuso (são os "criativos-fonte")

### Fase 3: Geração do áudio

Com o roteiro aprovado, chamar a API do Voicebox (`references/api-reference.md`):

```bash
curl -X POST http://127.0.0.1:17493/generate \
  -H "Content-Type: application/json" \
  -d '{
    "text": "<roteiro aprovado>",
    "profile_id": "<profile_id da voz do proprietário>",
    "language": "pt"
  }'
```

- Textos longos: o Voicebox faz chunking automático com crossfade; ainda assim, preferir roteiros ≤ 90s
- Se o servidor MCP do Voicebox estiver conectado à sessão, usar as tools MCP em vez de curl

### Fase 4: Controle de qualidade

Antes de aprovar o áudio para envio, verificar:

- [ ] Pronúncia correta de nomes próprios, marca da clínica e termos técnicos (se errar, reescrever foneticamente no roteiro — ex.: "Dra." → "doutora")
- [ ] Naturalidade da entonação (sem cortes bruscos entre chunks)
- [ ] Duração dentro do alvo do canal
- [ ] Identificação de automação presente (quando aplicável)
- [ ] Ouvir o áudio inteiro — nunca aprovar sem escutar

Reprovado → ajustar roteiro (pontuação e quebras de frase mudam a entonação) e regerar.

### Fase 5: Entrega e catálogo

1. Nomear o arquivo com padrão `AAAA-MM-DD_<publico>_<objetivo>.wav` (ex.: `2026-07-15_lead_consulta-automatizada.wav`)
2. Manter catálogo roteiro ↔ áudio para reuso em automações (n8n, CRM, WhatsApp)
3. Áudios recorrentes (boas-vindas, lembrete padrão) são gerados uma vez e reusados; áudios personalizados (com nome do paciente) são gerados sob demanda via API

## Referências

| Arquivo | Conteúdo |
|---------|----------|
| `references/voicebox-setup.md` | Instalação, clonagem da voz do proprietário, configuração MCP |
| `references/api-reference.md` | Endpoints REST do Voicebox e exemplos de integração |
| `references/script-templates.md` | Templates de roteiro pt-BR (lead, paciente, lembrete, follow-up) |

## Limites desta skill

- **Não** clonar vozes de terceiros, celebridades ou qualquer pessoa que não seja o proprietário com consentimento explícito
- **Não** gerar áudio com conteúdo médico prescritivo (diagnóstico, posologia) — áudios são informativos e de relacionamento
- **Não** enviar áudio diretamente ao paciente/lead a partir desta skill — a entrega é responsabilidade da automação de envio (n8n/CRM), com opt-in registrado
