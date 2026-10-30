# Documentação de API — [NOME DO MÓDULO OU SERVIÇO]

**Projeto:** `[Nome do Projeto]`  
**URL Base (Desenvolvimento):** `[Ex.: http://localhost:8080/api ou via proxy /api]`  
**Variável de Ambiente no Cliente:** `[Ex.: VITE_API_URL]`  
**Formato Padrão:** `application/json; charset=utf-8`  
**Status do Contrato:** `[Implementado e Verificado no Código | Contrato Proposto Pendente de Confirmação]`

---

## 1. Autenticação e Autorização Padrão

- **Mecanismo:** `[Ex.: Bearer Token JWT no header Authorization | Sessão | Público]`
- **Header Obrigatório:**
  ```http
  Authorization: Bearer <TOKEN_DE_ACESSO>
  ```
- **Perfis Permitidos:** `[Ex.: ADMIN, FUNCIONARIO, CLIENTE]`

---

## 2. Endpoints

### 2.1. `[MÉTODO HTTP]` `[/caminho/do/recurso]` — `[Resumo da finalidade]`

- **Descrição:** `[Explica o que o endpoint realiza e quando deve ser chamado]`
- **Autenticação Exigida:** `[Sim / Não]`
- **Permissões / Perfis:** `[Quais perfis podem acessar]`

#### Parâmetros de Rota (`Path Params`) e Consulta (`Query Params`)

| Nome | Local (`path` / `query`) | Tipo | Obrigatório? | Descrição / Restrições |
| :--- | :--- | :--- | :--- | :--- |
| `id` | `path` | `string (UUID)` | Sim | Identificador único do registro. |
| `status` | `query` | `string` | Não | Filtro por status (`PENDENTE`, `ENVIADO`, `ERRO`). |
| `page` | `query` | `integer` | Não | Página atual (padrão: `1`). |

#### Corpo da Requisição (`Request Body` — quando aplicável)

```json
{
  "clienteId": "8f14e45f-ceea-467a-a838-112233445566",
  "canal": "EMAIL",
  "mensagem": "Sua cota foi contemplada. Confira as próximas etapas no portal."
}
```

#### Respostas Possíveis (`Responses`)

- **`200 OK` / `201 Created` (Sucesso):**
  ```json
  {
    "id": "notif_01",
    "status": "ENVIADO",
    "processadoEm": "2026-10-29T20:00:00Z"
  }
  ```
- **`400 Bad Request` / `422 Unprocessable Content` (Erro de Validação):**
  ```json
  {
    "title": "Dados inválidos",
    "status": 422,
    "detail": "O campo 'canal' deve ser EMAIL ou WHATSAPP."
  }
  ```
- **`401 Unauthorized`:** Token ausente, inválido ou expirado.
- **`403 Forbidden`:** Usuário autenticado não possui permissão para este recurso.
- **`404 Not Found`:** Recurso não encontrado.
- **`500 Internal Server Error`:** Falha interna no processamento do servidor.

---

## 3. Limitações e Pendências Conhecidas

- `[Registrar explicitamente qualquer campo, integração externa ou comportamento que ainda dependa de implementação ou confirmação no back-end]`

