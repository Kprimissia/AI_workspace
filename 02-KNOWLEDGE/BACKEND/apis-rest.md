# Guia Técnico: Design e Integração de APIs RESTful

## 1. Visão Geral e Conceitos Fundamentais

Uma **API RESTful** modela funcionalidades como **recursos** identificados por URLs (substantivos no plural), manipulados por métodos HTTP padronizados e representados tipicamente em JSON (`application/json`).

### Semântica dos Métodos HTTP e Idempotência

| Método | Finalidade | Idempotente? | Seguro (Read-Only)? | Código de Sucesso Típico |
| :--- | :--- | :--- | :--- | :--- |
| **`GET`** | Consultar um recurso ou coleção | Sim | Sim | `200 OK` |
| **`POST`** | Criar novo recurso ou disparar processamento | Não (salvo `Idempotency-Key`) | Não | `201 Created` / `202 Accepted` |
| **`PUT`** | Substituir integralmente um recurso existente | Sim | Não | `200 OK` / `204 No Content` |
| **`PATCH`** | Atualizar parcialmente campos de um recurso | Não necessariamente | Não | `200 OK` |
| **`DELETE`** | Remover um recurso | Sim | Não | `204 No Content` / `200 OK` |

---

## 2. Boas Práticas de Design e Consumo

1. **Nomenclatura Limpa de Rotas:**
   - Use substantivos no plural e *kebab-case*: `/api/clientes-contemplados/{id}/notificacoes`.
   - Evite verbos na URL (`/api/criarCliente` ou `/api/getNotificacoes`). Ações operacionais específicas podem usar sub-recursos claros como `POST /api/notificacoes/{id}/reenvio`.
2. **Códigos de Status HTTP Precisos (RFC 9110):**
   - `200 OK` (sucesso com corpo), `201 Created` (recurso criado + header `Location`), `204 No Content` (sucesso sem corpo).
   - `400 Bad Request` (JSON malformado ou sintaxe inválida), `401 Unauthorized` (não autenticado/token inválido), `403 Forbidden` (autenticado, mas sem permissão), `404 Not Found` (recurso inexistente), `409 Conflict` (conflito de estado/duplicidade), `422 Unprocessable Content` (erro de validação de campos/regras), `429 Too Many Requests` (limite de taxa excedido).
   - `500 Internal Server Error` (erro inesperado no servidor), `502 Bad Gateway` / `503 Service Unavailable` / `504 Gateway Timeout` (falha em serviço externo).
3. **Padronização de Respostas de Erro (RFC 9457 — Problem Details):**
   - Retorne objetos estruturados contendo `type`, `title`, `status`, `detail` e `errors` (mapa de campos inválidos), nunca expondo *stack traces* ou nomes de tabelas do banco.
4. **Paginação, Filtros e Ordenação em Coleções:**
   - Nunca retorne tabelas inteiras sem limite. Utilize query params padronizados: `GET /api/notificacoes?page=1&pageSize=20&status=PENDENTE&sort=-criadoEm`.

---

## 3. Exemplos Práticos

### 3.1. Contrato Padronizado de Paginação e Erro (JSON)

```json
// GET /api/notificacoes?page=1&pageSize=20 -> 200 OK
{
  "data": [
    {
      "id": "notif_9821",
      "clienteNome": "Maria Silva",
      "canal": "EMAIL",
      "status": "ENVIADO",
      "atualizadoEm": "2026-10-29T18:30:00Z"
    }
  ],
  "meta": {
    "page": 1,
    "pageSize": 20,
    "totalItems": 142,
    "totalPages": 8
  }
}
```

```json
// POST /api/notificacoes -> 422 Unprocessable Content (RFC 9457)
{
  "type": "https://api.exemplo.com/errors/validation-error",
  "title": "Falha na validação dos dados enviados",
  "status": 422,
  "detail": "Um ou mais campos obrigatórios estão inválidos.",
  "errors": {
    "email": ["O endereço de e-mail informado não é válido."],
    "cota": ["O número da cota deve ser maior que zero."]
  }
}
```

---

## 4. Erros Comuns e Como Evitá-los

| Erro Comum | Problema | Solução Recomendada |
| :--- | :--- | :--- |
| **Retornar `200 OK` com `{ "success": false, "error": "..." }`** | Quebra a semântica HTTP, proxies, caches e o tratamento de erros em clientes HTTP. | Retornar o código HTTP real (`400`, `401`, `403`, `404`, `422`, `500`) acompanhado do JSON de erro. |
| **Confundir `401 Unauthorized` com `403 Forbidden`** | Retornar `403` quando o token expirou impede que o front-end redirecione para o login ou renove o token. | Usar `401` quando falta autenticação válida e `403` apenas quando o usuário está autenticado mas não tem perfil/permissão para o recurso. |
| **Criar endpoints fictícios no Front-end** | Assumir que uma rota existe no servidor apenas porque há uma tela desenhada gera falhas silenciosas ou quebras na integração. | Inspecionar o repositório de back-end ou documentação OpenAPI/Swagger antes de integrar. |

---

## 5. Referências Oficiais

- **MDN HTTP Status Codes & Methods:** https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status
- **RFC 9110 — HTTP Semantics:** https://httpwg.org/specs/rfc9110.html
- **RFC 9457 — Problem Details for HTTP APIs:** https://www.rfc-editor.org/rfc/rfc9457.html
- **OpenAPI Specification (OAS 3.1):** https://spec.openapis.org/oas/latest.html

