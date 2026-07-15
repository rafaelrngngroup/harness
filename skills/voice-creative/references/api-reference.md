# Voicebox — Referência de API para Integração

API REST local do Voicebox em `http://127.0.0.1:17493` (documentação interativa completa em `/docs`). Sem autenticação própria — manter em rede privada.

## Endpoints principais

### `POST /generate` — gerar áudio com voz clonada

O endpoint central desta skill: texto → áudio com o perfil de voz do proprietário.

```bash
curl -X POST http://127.0.0.1:17493/generate \
  -H "Content-Type: application/json" \
  -d '{
    "text": "Olá, aqui é o Rafael. Vou te explicar rapidinho como funciona a nossa consulta...",
    "profile_id": "<profile_id>",
    "language": "pt"
  }'
```

- `text` — roteiro aprovado (pt-BR). Textos longos sofrem chunking automático com crossfade
- `profile_id` — perfil da voz clonada (obter via `GET /profiles`)
- `language` — `"pt"` para português (engine Chatterbox Multilingual)

### `GET /profiles` — listar perfis de voz

```bash
curl http://127.0.0.1:17493/profiles
```

Usar para descobrir/validar o `profile_id` antes de gerar.

### `POST /speak` — saída de voz para agentes

Fala o texto no dispositivo local (útil para testes rápidos, não para arquivos de criativo):

```bash
curl -X POST http://127.0.0.1:17493/speak \
  -H "Content-Type: application/json" \
  -H "X-Voicebox-Client-Id: harness" \
  -d '{"text": "Teste concluído.", "profile": "voz-rafael"}'
```

### `POST /transcribe` — transcrição (Whisper)

Útil no fluxo inverso: transcrever áudios recebidos de pacientes/leads para a automação processar.

```bash
curl -X POST http://127.0.0.1:17493/transcribe \
  -F "audio=@recebido.wav" \
  -F "model=whisper-turbo"
```

## Integração com a automação (n8n)

Padrão recomendado para envio de áudio personalizado a um lead/paciente:

1. **Trigger** — evento no CRM/WhatsApp (novo lead, consulta agendada)
2. **Montagem do roteiro** — nó que preenche o template com nome/contexto (ver `script-templates.md`)
3. **HTTP Request** — `POST http://<host-voicebox>:17493/generate` com `text`, `profile_id` (de variável de ambiente `VOICEBOX_PROFILE_ID`) e `language: "pt"`
4. **Envio** — anexar o áudio retornado na mensagem de WhatsApp/e-mail
5. **Registro** — logar roteiro usado + destinatário + opt-in

Áudios **não personalizados** (boas-vindas padrão, explicação da consulta automatizada) devem ser gerados uma vez, revisados por escuta completa e armazenados — a automação apenas anexa o arquivo pronto, sem chamar o `/generate` a cada envio.

## MCP (alternativa a REST)

Com o servidor MCP conectado (`claude mcp add voicebox ...` — ver `voicebox-setup.md` §4), o Claude Code acessa geração e perfis como tools nativas, dispensando curl. Preferir MCP em sessões interativas; preferir REST em automações (n8n).

## Tratamento de erros

- **Conexão recusada** → Voicebox não está rodando; subir o app/`docker compose up`
- **Perfil não encontrado** → conferir `profile_id` via `GET /profiles`
- **Áudio com pronúncia errada** → não é erro de API; ajustar grafia fonética no roteiro e regerar
- **Geração lenta** → esperado em CPU; avaliar GPU para volume de produção
