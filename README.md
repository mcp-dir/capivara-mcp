# Capivara: Investigação Cadastral

### Capivara: Investigação Cadastral para Claude, ChatGPT e agentes de IA

Raio-X cadastral 360º de uma pessoa (ou empresa) a partir de nome + CPF: identidade, contato, dinheiro a receber (Valores a Receber do BC, IRPF, benefícios), crédito, antecedentes/sanções, societário, veículos e processos, num relatório único. Preço fixo por consulta (pré-pago), em 3 níveis. Hospedado pela plataforma, sem credenciais.

- 📊 **3 ferramentas**
- 🔒 **Somente leitura**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `Capivara: Investigação Cadastral` e **URL** `https://api.mcp.ai/p_capivara`.

### Cursor

[➕ Instalar Capivara: Investigação Cadastral no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=capivara&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9jYXBpdmFyYSJ9)

### VS Code (Copilot Chat)

[➕ Instalar Capivara: Investigação Cadastral no VS Code](vscode:mcp/install?name=capivara&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_capivara%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_capivara
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Monte um dossiê básico do CPF 000.000.000-00 (nome: Fulano de Tal)
Faça uma investigação nível médio dessa pessoa (crédito + antecedentes)
Raio-X completo (avançado) com societário e processos
```

---

## 3 ferramentas disponíveis

| Tool | Descrição |
|---|---|
| `capivara_resolver` | CAMADA 1 (descoberta de identidade): a partir do que você SABE da pessoa em TEXTO LIVRE (nome, cidade, emprego, empresa, qualquer pista), descobre o CPF mais provável e devolve um PERFIL NORMALIZADO (nome, CPF, empres… |
| `capivara_registrar_consentimento` | Registra, de forma auditável (LGPD), a finalidade e a base legal de uma investigação — e, quando aplicável, a DECLARAÇÃO do usuário de que tem autorização do titular para dados sob sigilo (SCR/Bacen, cadastro positivo). |
| `capivara_dossie` | Raio-X cadastral 360º de uma PESSOA (por CPF) OU EMPRESA (por CNPJ) — consolidado num relatório por seção. |

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Pré-pago (carteira de créditos), paga por uso. Veja [docs/precos.md](docs/precos.md).

---

## Privacidade & LGPD

- **Somente leitura**, nenhuma ferramenta altera dados na origem.
- **Sub-processadores**: o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_capivara`.


---

## Suporte

- 📧 [capivara@mcp.ai](mailto:capivara@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/capivara-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_capivara` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
