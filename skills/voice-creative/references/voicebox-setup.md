# Voicebox — Setup e Clonagem de Voz

Guia de preparação do [Voicebox](https://github.com/jamiepine/voicebox) (MIT License) para gerar áudios com a voz clonada do proprietário. Feito uma única vez; depois disso a skill `voice-creative` só consome a API.

## 1. Instalação

Escolher uma das opções:

| Opção | Quando usar | Como |
|-------|-------------|------|
| **App desktop (macOS)** | Máquina pessoal Apple Silicon/Intel | Baixar o DMG nas releases do repositório |
| **App desktop (Windows)** | Máquina pessoal Windows | Baixar o MSI nas releases |
| **Docker** | Servidor/VPS da automação (recomendado para integração com n8n) | `docker compose up` na raiz do repositório clonado |
| **Build from source** | Linux sem Docker | Seguir instruções do README do projeto |

Stack: Tauri + React (desktop), FastAPI (backend Python), inferência via MLX (Apple Silicon) ou PyTorch (CUDA/ROCm/CPU).

**Hardware:** roda em CPU (mais lento). GPU acelera bastante — LuxTTS usa ~1 GB de VRAM; Chatterbox Multilingual (a engine para português) se beneficia de GPU dedicada. Para produção com volume, preferir servidor com GPU NVIDIA.

Após subir, a API fica em `http://127.0.0.1:17493` e a documentação interativa em `http://127.0.0.1:17493/docs`.

## 2. Escolha da engine (português)

O Voicebox traz 7 engines de TTS. Para pt-BR com clonagem de voz:

- **Chatterbox Multilingual** ✅ — 23 idiomas, incluindo português, com clonagem zero-shot. **É a engine desta skill.**
- Qwen3-TTS — 10 idiomas, português não listado. Não usar.
- Kokoro / LuxTTS / Chatterbox Turbo — leves, mas foco em inglês ou sem clonagem multilíngue. Não usar para os criativos.

## 3. Clonagem da voz do proprietário

A clonagem é **zero-shot**: uma única amostra de referência de boa qualidade é suficiente.

### 3.1 Gravar a amostra de referência

- **Duração**: 30 segundos a 2 minutos de fala contínua e natural
- **Conteúdo**: fala espontânea em pt-BR, no tom que os áudios finais devem ter (ex.: explicando a clínica para um paciente)
- **Qualidade**: ambiente silencioso, sem eco, microfone a ~15 cm; celular em ambiente silencioso funciona
- **Formato**: WAV de preferência (o app aceita gravação direta)
- **Evitar**: música de fundo, outras vozes, leitura robótica

### 3.2 Criar o perfil de voz

**Pelo app desktop:** aba de vozes → criar perfil → enviar/gravar a amostra → nomear (ex.: `voz-rafael`).

**Pela API/interface web (Docker):** usar a rota de criação de perfil documentada em `/docs` (upload da amostra de referência).

### 3.3 Obter o `profile_id`

```bash
curl http://127.0.0.1:17493/profiles
```

Anotar o `profile_id` do perfil criado — ele é usado em toda chamada de geração. Registrar no ambiente da automação (ex.: variável `VOICEBOX_PROFILE_ID` no n8n).

### 3.4 Validar a clonagem

Gerar um áudio de teste e ouvir por completo:

```bash
curl -X POST http://127.0.0.1:17493/generate \
  -H "Content-Type: application/json" \
  -d '{"text": "Olá! Este é um teste da minha voz clonada para os criativos da clínica.", "profile_id": "<profile_id>", "language": "pt"}'
```

Se a semelhança estiver baixa: regravar a amostra com melhor qualidade (o fator dominante é a qualidade da referência).

## 4. Integração MCP (opcional, recomendado)

O Voicebox expõe um servidor MCP — permite que o Claude Code gere áudios por tools nativas em vez de curl:

```bash
claude mcp add voicebox \
  --transport http \
  --url http://127.0.0.1:17493/mcp \
  --header "X-Voicebox-Client-Id: claude-code"
```

Para outros clientes MCP (config JSON):

```json
{
  "mcpServers": {
    "voicebox": {
      "url": "http://127.0.0.1:17493/mcp",
      "headers": { "X-Voicebox-Client-Id": "claude-code" }
    }
  }
}
```

> Se o Voicebox rodar em servidor remoto (Docker na VPS), trocar `127.0.0.1` pelo host correspondente e proteger o acesso (rede privada/VPN — a API não tem autenticação própria; **nunca expor a porta 17493 à internet pública**, pois qualquer pessoa com acesso poderia gerar áudios com a voz clonada).

## 5. Segurança e conformidade

- A amostra de voz e o perfil clonado são **dados pessoais sensíveis do proprietário** — manter na infraestrutura própria (o Voicebox é local-first, nada vai para nuvem de terceiros)
- Restringir quem pode chamar a API de geração (rede privada, firewall)
- Registrar consentimento/opt-in dos destinatários antes de enviar áudios pela automação (LGPD)
- Nos áudios automatizados, identificar que a mensagem faz parte da automação da clínica (ver templates)
