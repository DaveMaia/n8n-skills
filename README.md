# n8n-skills

Kit de **skills especializadas para agentes de IA** criarem workflows n8n com qualidade de produção usando o servidor MCP **n8n-mcp**.

> Projeto otimizado para execução em ambientes agent-first (incluindo **Google Antigravity**) sem perder compatibilidade com Claude Code, Claude.ai e uso via API.

---

## 1) Objetivo do projeto

Este repositório existe para reduzir os erros mais comuns quando um agente tenta construir workflows n8n de forma programática:

- uso incorreto das ferramentas MCP;
- erros de sintaxe de expressão (`{{ ... }}`);
- configuração incompleta/inconsistente de nós;
- loops de validação;
- escolha ruim de arquitetura de workflow.

A proposta é fornecer instruções modulares (skills) que podem ser compostas dinamicamente conforme o tipo de tarefa.

---

## 2) Escopo atual (v1.4.x)

O pacote contém **7 skills complementares**:

1. **n8n-expression-syntax**
2. **n8n-mcp-tools-expert**
3. **n8n-workflow-patterns**
4. **n8n-validation-expert**
5. **n8n-node-configuration**
6. **n8n-code-javascript**
7. **n8n-code-python**

Cada skill possui:

- `SKILL.md` (núcleo da skill)
- arquivos de referência (`COMMON_*`, `EXAMPLES`, guias específicos etc.)
- `README.md` local com metadados

---

## 3) Arquitetura do repositório

```text
n8n-skills/
├── skills/                        # Implementações das 7 skills
├── evaluations/                   # Cenários de validação por domínio
├── docs/                          # Instalação, uso, dev e guias de operação
├── dist/                          # Artefatos zip para distribuição
├── AGENTS.md                      # Regras operacionais para agentes
├── GEMINI.md                      # Guardrails agent-first (Antigravity-ready)
├── build.sh                       # Script de empacotamento
└── README.md
```

---

## 4) Compatibilidade de plataformas

### Claude Code
- Instalação via plugin (`/plugin install`) ou zip bundle.

### Claude.ai / Claude Desktop
- Upload das skills em zips individuais.

### API / SDK
- Carregamento das skills como instruções externas em pipelines de agentes.

### Google Antigravity (agent-first)
- O repositório inclui:
  - `AGENTS.md` para regras operacionais cross-agent;
  - `GEMINI.md` para fluxo recomendado de execução, verificação e entrega;
  - `docs/ANTIGRAVITY_BEST_PRACTICES.md` para práticas comunitárias e templates de prompt.

---

## 5) Como instalar

## Pré-requisitos

1. n8n-mcp instalado/configurado
2. ambiente com suporte a skills/agentes
3. (opcional) credenciais da API do n8n para operações de criação/gestão de workflow

### Opção A — Claude Code (recomendada)

```bash
/plugin install czlonkowski/n8n-skills
```

ou manualmente:

```bash
git clone https://github.com/czlonkowski/n8n-skills.git
cp -r n8n-skills/skills/* ~/.claude/skills/
```

### Opção B — Claude.ai / Desktop

- Use os zips individuais em `dist/`
- Faça upload um por vez em **Settings → Capabilities → Skills**

### Opção C — Bundle completo

- Use `dist/n8n-mcp-skills-v1.4.0.zip` em ambientes compatíveis com estrutura de plugin completa.

---

## 6) Uso prático

As skills ativam por intenção da consulta.

Exemplos:

- “Como escrever expressão n8n com `$json.body`?” → `n8n-expression-syntax`
- “Encontre o node Slack e valide config” → `n8n-mcp-tools-expert` + `n8n-validation-expert`
- “Monte workflow webhook → transformação → notificação” → `n8n-workflow-patterns`
- “Erro no Code node JS / formato de retorno” → `n8n-code-javascript`

---

## 7) Qualidade e desenvolvimento

O projeto segue uma abordagem orientada a avaliação:

1. definir cenários (`evaluations/*`)
2. ajustar skill de forma mínima e objetiva
3. validar comportamento esperado
4. iterar até consistência

Diretrizes de contribuição:

- priorizar exemplos reais/reproduzíveis;
- evitar `SKILL.md` excessivamente longo;
- manter documentação e empacotamento sincronizados.

Veja também:

- `docs/DEVELOPMENT.md`
- `docs/MCP_TESTING_LOG.md`

---

## 8) Empacotamento

Para gerar artefatos:

```bash
./build.sh
```

O build gera:

- zips individuais por skill (Claude.ai/Desktop)
- zip bundle completo (Claude Code e ambientes compatíveis)

O bundle inclui `.claude-plugin/`, `skills/`, `README.md`, `LICENSE`, `AGENTS.md` e `GEMINI.md`.

---

## 9) Documentação principal

- `docs/INSTALLATION.md`
- `docs/USAGE.md`
- `docs/DEVELOPMENT.md`
- `docs/ANTIGRAVITY_BEST_PRACTICES.md`
- `dist/README.md`

---

## 10) Licença

MIT — veja `LICENSE`.

## Créditos

Concebido por Romuald Członkowski.
Parte do ecossistema do projeto n8n-mcp.
