---
name: capivara-mcp
description: Skill da REST API do Capivara: Investigação Cadastral na MCP.AI: 3 endpoints em /api/capivara. Raio-X cadastral 360º de uma pessoa (ou empresa) a partir de nome + CPF: identidade, contato, dinheiro a receber (Valores a Receber do BC, IRPF, benefícios), crédito, antecedentes/sanções, societário, veículos e processos, num relatório único. Preço fixo por consulta (pré-pago), em 3 níveis. Hospedado pela plataforma, sem credenciais. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# Capivara: Investigação Cadastral — REST API skill

Você tem acesso à **Capivara: Investigação Cadastral** REST API na MCP.AI.

> Raio-X cadastral 360º de uma pessoa (ou empresa) a partir de nome + CPF: identidade, contato, dinheiro a receber (Valores a Receber do BC, IRPF, benefícios), crédito, antecedentes/sanções, societário, veículos e processos, num relatório único. Preço fixo por consulta (pré-pago), em 3 níveis. Hospedado pela plataforma, sem credenciais.

## Base URL

```
https://api.mcp.ai/api/capivara
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/capivara/dossie \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/capivara/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (3)

#### `capivara_dossie`

Raio-X cadastral 360º de uma PESSOA (por CPF) OU EMPRESA (por CNPJ) — consolidado num relatório por seção. _(POST /api/capivara/dossie)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `nome` | string | Não | Nome completo do investigado (melhora antecedentes/sanções; obrigatório p/ processos). |
| `cpf` | string | Não | CPF do investigado (pessoa física). Informe cpf OU cnpj. |
| `cnpj` | string | Não | CNPJ (pessoa jurídica). Informe cpf OU cnpj. |
| `nivel` | string | Não | Profundidade/preço do dossiê: basico (R$15), medio (R$49), avancado (R$99). Default basico. (basico, medio, avancado) |
| `formato` | string | Não | **resumo** (default): devolve um digest (status de cada fonte + destaques) e o dossiê INTEIRO vai num arquivo .md, aberto por seção com `arquivo_ler(file_id, secao)`. É o modo certo pra conversa: o completo passa de 100 mil tokens e estoura o contexto. **completo**: todas as seções na resposta (use só se for processar o JSON inteiro por programa, ex.: integração REST). (resumo, completo) |
| `autorizacao_titular_scr` | boolean | Não | Declara que o usuário tem AUTORIZAÇÃO do titular para dados sob sigilo (SCR/Bacen e relatório de crédito positivo). Só marque true após confirmar com o usuário. Sem isso, esses itens são pulados (o resto do dossiê roda normalmente). |

#### `capivara_registrar_consentimento`

Registra, de forma auditável (LGPD), a finalidade e a base legal de uma investigação — e, quando aplicável, a DECLARAÇÃO do usuário de que tem autorização do titular para dados sob sigilo (SCR/Bacen, _(POST /api/capivara/registrar/consentimento)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `cpf` | string | Não | CPF do titular investigado (informe cpf OU cnpj). |
| `cnpj` | string | Não | CNPJ investigado (informe cpf OU cnpj). |
| `finalidade` | string | Sim | Finalidade da consulta (ex.: 'prevenção à fraude em contratação', 'due diligence de fornecedor'). |
| `base_legal` | string | Sim | Base legal LGPD que ampara o tratamento. (prevencao_fraude, obrigacao_legal, legitimo_interesse, exercicio_de_direitos, consentimento_do_titular, protecao_ao_credito) |
| `autorizacao_titular` | boolean | Não | Declara que o usuário tem autorização do titular para dados sob sigilo (SCR/cadastro positivo). Marque true só após confirmar com o usuário. |
| `observacao` | string | Não | Observação livre (ex.: nº do contrato/processo que justifica). |

#### `capivara_resolver`

CAMADA 1 (descoberta de identidade): a partir do que você SABE da pessoa em TEXTO LIVRE (nome, cidade, emprego, empresa, qualquer pista), descobre o CPF mais provável e devolve um PERFIL NORMALIZADO ( _(POST /api/capivara/resolver)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `texto` | string | Não | Tudo que você sabe da pessoa, em texto livre: nome completo, cidade, emprego, empresa, cônjuge, qualquer pista. Quanto mais informação, maior a precisão. |
| `cnpj` | string | Não | CNPJ de uma empresa da pessoa, se você já tiver (atalho: pula a busca na web). |
| `seguir_dossie` | boolean | Não | Se true e o CPF for confirmado, já emite o `capivara_dossie` 360º na sequência (cobra o nível por cima). |
| `nivel` | string | Não | Nível do dossiê quando seguir_dossie=true (default basico). (basico, medio, avancado) |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_capivara` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
