# Teste Técnico - Catálogo Siscomex

## Contexto

A empresa atua como despachante e possui acesso ao Portal Único Siscomex.  
O objetivo deste teste é construir uma solução para disponibilizar aos clientes a consulta do catálogo de produtos, atributos e métricas, sem permitir alterações diretas pelo cliente.

A API real do Portal Único não deve ser acessada.  
A documentação oficial pode ser consultada apenas para contexto:

https://docs.portalunico.siscomex.gov.br/api/catp/

---

## Objetivo

Desenvolver uma solução composta por:

- API REST em ASP.NET Core
- Banco de dados SQL Server ou PostgreSQL
- Aplicação WinForms consumindo a API
- Autenticação JWT
- Controle de perfis Cliente/Admin
- Importação de catálogo mock
- Tradução e validação de atributos por NCM
- Fluxo de solicitação e aprovação de alterações

---

## Arquivos fornecidos

| Arquivo | Descrição |
|---|---|
| `catalogo_mock_20_itens_anonimizado.json` | Mock do catálogo de produtos |
| `ATRIBUTOS_POR_NCM_2026_04_29.json` | Base de atributos por NCM |
| `teste_tecnico_catalogo_siscomex.pdf` | Enunciado completo do teste |

---

## Requisitos obrigatórios

### API

- ASP.NET Core
- Entity Framework Core
- SQL Server ou PostgreSQL
- JWT
- Roles/Claims para Cliente e Administrador
- Injeção de dependência
- Interfaces para services e repositories
- DTOs separados das entidades
- Middleware global de tratamento de erros
- Logs com `ILogger` ou equivalente
- Migrations ou script de banco

---

## Login

O sistema deve possuir login real.

Não devem ser usados usuários fixos no enunciado.  
O candidato deve implementar uma forma de criar usuários reais com perfis:

- Cliente
- Administrador

As senhas devem ser armazenadas com hash seguro.

---

## Regras de negócio

- Cliente pode consultar o catálogo.
- Cliente não pode alterar dados diretamente.
- Cliente pode solicitar alterações.
- Toda solicitação inicia como `Pendente`.
- Administrador pode aprovar ou rejeitar solicitações.
- Solicitação aprovada deve simular envio ao Portal Único.
- Toda aprovação, rejeição e envio deve gerar log/histórico.

---

## Atributos por NCM

Os produtos possuem atributos por código, exemplo:

```json
{
  "atributo": "ATT_14545",
  "valor": "82"
}
