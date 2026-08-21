# Ferramentas

Capivara: Investigação Cadastral expõe 3 ferramentas (todas somente leitura).

### 1. `capivara_resolver`
**Input**: `texto` (opcional), `cnpj` (opcional), `seguir_dossie` (opcional), `nivel` (opcional)

CAMADA 1 (descoberta de identidade): a partir do que você SABE da pessoa em TEXTO LIVRE (nome, cidade, emprego, empresa, qualquer pista), descobre o CPF mais provável e devolve um PERFIL NORMALIZADO (nome, CPF, empres…

### 2. `capivara_registrar_consentimento`
**Input**: `cpf` (opcional), `cnpj` (opcional), `finalidade`, `base_legal`, `autorizacao_titular` (opcional), `observacao` (opcional)

Registra, de forma auditável (LGPD), a finalidade e a base legal de uma investigação — e, quando aplicável, a DECLARAÇÃO do usuário de que tem autorização do titular para dados sob sigilo (SCR/Bacen, cadastro positivo).

### 3. `capivara_dossie`
**Input**: `nome` (opcional), `cpf` (opcional), `cnpj` (opcional), `nivel` (opcional), `formato` (opcional), `autorizacao_titular_scr` (opcional)

Raio-X cadastral 360º de uma PESSOA (por CPF) OU EMPRESA (por CNPJ) — consolidado num relatório por seção.

## Prompts de exemplo

```
Monte um dossiê básico do CPF 000.000.000-00 (nome: Fulano de Tal)
Faça uma investigação nível médio dessa pessoa (crédito + antecedentes)
Raio-X completo (avançado) com societário e processos
```
