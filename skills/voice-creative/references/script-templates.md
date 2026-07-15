# Templates de Roteiro — Criativos de Voz (pt-BR)

Roteiros-base para os áudios com a voz clonada do proprietário. Regras gerais:

- **Tom falado**: frases curtas, linguagem natural, como se estivesse mandando um áudio de WhatsApp de verdade
- **Duração**: 30–60s (~80–150 palavras) para WhatsApp; nunca passar de 90s
- **Placeholders**: `{{nome}}`, `{{clinica}}`, `{{data}}`, `{{hora}}` — preencher antes de gerar
- **Pronúncia**: escrever por extenso o que o TTS pode errar ("Dra." → "doutora"; siglas → soletradas ou por extenso)
- **Identificação de automação**: obrigatória em áudios disparados automaticamente (marcada nos templates)
- Todo roteiro novo ou alterado passa por aprovação do proprietário antes de gerar o áudio

---

## T1 — Lead: como funciona a consulta pela automação

**Uso**: enviado ao lead que demonstrou interesse, explicando a consulta feita pela automação da clínica.

> Oi, {{nome}}! Aqui é o Rafael, da {{clinica}}. Que bom que você chegou até a gente!
> Deixa eu te explicar rapidinho como funciona a nossa consulta. A gente usa uma automação que cuida de toda a parte burocrática pra você: o agendamento, os lembretes e as orientações chegam direto aqui no seu WhatsApp, no seu tempo, sem você precisar ficar ligando pra clínica.
> No dia da consulta, o atendimento é normal, com toda a atenção que você merece — a automação só deixa tudo mais fácil antes e depois.
> Se você quiser agendar ou tirar qualquer dúvida, é só responder essa mensagem. Essa resposta chega pra nossa equipe na hora. Até já!

*Este áudio é enviado pela automação da clínica com a voz do Rafael.* ← manter no texto da mensagem que acompanha o áudio.

---

## T2 — Lead: boas-vindas + próximo passo

**Uso**: primeira resposta automática a um novo lead.

> Oi, {{nome}}, tudo bem? Aqui é o Rafael, da {{clinica}}. Recebi o seu contato e já quero te dar as boas-vindas!
> Pra gente te atender do melhor jeito, me conta em uma mensagem o que você está buscando. Pode ser por texto ou por áudio mesmo.
> Assim que você responder, nossa equipe já te retorna com os próximos passos. Combinado? Até daqui a pouco!

---

## T3 — Paciente: confirmação e preparo da consulta

**Uso**: após o agendamento, confirmando data e explicando o que esperar.

> Oi, {{nome}}! Aqui é o Rafael, da {{clinica}}. Passando pra confirmar a sua consulta no dia {{data}}, às {{hora}}.
> Você vai receber por aqui, automaticamente, um lembrete um dia antes e as orientações de preparo, se precisar de alguma.
> Se tiver qualquer imprevisto, é só responder essa mensagem que a gente remarca sem burocracia. Te espero lá!

---

## T4 — Paciente: lembrete de consulta (véspera)

**Uso**: disparo automático um dia antes da consulta.

> Oi, {{nome}}! Lembrete rápido da {{clinica}}: sua consulta é amanhã, dia {{data}}, às {{hora}}.
> Se estiver tudo certo, não precisa responder nada. Se precisar remarcar, é só mandar uma mensagem por aqui. Até amanhã!

---

## T5 — Paciente: follow-up pós-consulta

**Uso**: disparo automático alguns dias após a consulta.

> Oi, {{nome}}! Aqui é o Rafael, da {{clinica}}. Passando pra saber como você está depois da consulta.
> Qualquer dúvida que tiver aparecido, pode mandar por aqui — sua mensagem chega direto pra nossa equipe.
> Cuida de você, e conta com a gente!

---

## Diretrizes de conteúdo

- **Nunca** incluir nos áudios: diagnóstico, prescrição, posologia, promessa de resultado clínico. Criativos são informativos e de relacionamento.
- **Sempre** dar um caminho de resposta humana ("é só responder essa mensagem").
- Personalização com `{{nome}}` exige geração sob demanda via API; versões sem nome ("Oi, tudo bem?") podem ser pré-geradas e reusadas.
- Ao criar template novo, seguir a estrutura: saudação + quem fala → mensagem única e clara → próximo passo → despedida curta.
