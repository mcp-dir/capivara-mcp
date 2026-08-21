# Capivara: Investigação Cadastral

### Capivara: Investigação Cadastral for Claude, ChatGPT and AI agents

360º background dossier on a person (or company) from name + CPF: identity, contact, money-to-claim (Central Bank unclaimed funds, income-tax, benefits), credit, criminal records/sanctions, corporate ties, vehicles and lawsuits, in a single report. Flat price per query (prepaid), in 3 tiers. Platform-hosted, no credentials.

- 📊 **3 tools**
- 🔒 **Read-only**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Portuguese version](README.md) · [Full docs (PT-BR)](docs/)

---

## One-click install

### Claude (Web and Desktop)

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

Manual: [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → name `Capivara: Investigação Cadastral`, URL `https://api.mcp.ai/p_capivara`.

### Cursor

[➕ Install in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=capivara&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9jYXBpdmFyYSJ9)

### VS Code (Copilot Chat)

[➕ Install in VS Code](vscode:mcp/install?name=capivara&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_capivara%22%7D)

### Any other MCP-over-HTTP client

```
https://api.mcp.ai/p_capivara
```

---

## 3 tools

| Tool | Description |
|---|---|
| `capivara_resolver` | CAMADA 1 (descoberta de identidade): a partir do que você SABE da pessoa em TEXTO LIVRE (nome, cidade, emprego, empresa, qualquer pista), descobre o CPF mais provável e devolve um PERFIL NORMALIZADO (nome, CPF, empres… |
| `capivara_registrar_consentimento` | Registra, de forma auditável (LGPD), a finalidade e a base legal de uma investigação — e, quando aplicável, a DECLARAÇÃO do usuário de que tem autorização do titular para dados sob sigilo (SCR/Bacen, cadastro positivo). |
| `capivara_dossie` | Raio-X cadastral 360º de uma PESSOA (por CPF) OU EMPRESA (por CNPJ) — consolidado num relatório por seção. |

---

## Pricing

See [docs/precos.md](docs/precos.md) (PT-BR).

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_capivara` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
