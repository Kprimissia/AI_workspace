# Guia Técnico: Bancos de Dados, Modelagem e Migrations

## 1. Visão Geral e Conceitos Fundamentais

O gerenciamento de persistência exige integridade referencial, segurança contra injeção, controle transacional (**ACID**) e evolução controlada de esquema via **Migrations**.

### Conceitos Essenciais
- **Propriedades ACID (Bancos Relacionais — PostgreSQL, MySQL, SQL Server):**
  - **Atomicidade:** A transação inteira é confirmada (`COMMIT`) ou revertida (`ROLLBACK`).
  - **Consistência:** Todas as restrições (`NOT NULL`, `UNIQUE`, `CHECK`, `FOREIGN KEY`) são respeitadas.
  - **Isolamento:** Transações concorrentes não interferem de forma inconsistente umas nas outras.
  - **Durabilidade:** Dados confirmados persistem mesmo em caso de falha do servidor.
- **Normalização (1FN, 2FN, 3FN):** Elimina redundância de dados e anomalias de atualização.
- **Migrations Versionadas (Flyway, Liquibase, Prisma Migrate, Alembic):** Todo ajuste estrutural em tabelas, colunas ou índices deve ser registrado em arquivos de migration versionados no Git, nunca aplicado manualmente em produção.

---

## 2. Boas Práticas de Modelagem e Consultas

1. **Consultas Parametrizadas (*Prepared Statements*):**
   - Nunca concatene variáveis de usuário em strings SQL. Utilize sempre *bind parameters* (`?`, `$1`, `:nome`) ou construtores parametrizados do ORM.
2. **Restrições no Próprio Banco de Dados:**
   - Validações na aplicação não substituem `NOT NULL`, `UNIQUE`, `FOREIGN KEY` e `CHECK` no esquema do banco, pois condições de corrida (*race conditions*) podem contornar verificações em memória.
3. **Indexação Estratégica:**
   - Crie índices (`CREATE INDEX`) para chaves estrangeiras (`FOREIGN KEY`) e colunas frequentemente usadas em cláusulas `WHERE`, `JOIN` e `ORDER BY`.
   - Evite criar índices desnecessários em todas as colunas, pois cada índice adicional degrada o desempenho de `INSERT`, `UPDATE` e `DELETE`.
4. **Migrations Seguras (*Expand and Contract*):**
   - Evite renomear ou excluir colunas diretamente em sistemas ativos sem verificar compatibilidade com a versão em execução.
   - Nunca execute comandos destrutivos (`DROP TABLE`, `TRUNCATE`, `DELETE` sem `WHERE`) sem backup confirmado e autorização explícita.

---

## 3. Exemplos Práticos

### 3.1. Modelagem Relacional com Integridade e Índices (PostgreSQL)

```sql
CREATE TABLE clientes_contemplados (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    nome VARCHAR(150) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE,
    numero_cota INTEGER NOT NULL CHECK (numero_cota > 0),
    criado_em TIMESTAMPTZ NOT NULL DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE notificacoes_envio (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    cliente_id UUID NOT NULL REFERENCES clientes_contemplados(id) ON DELETE RESTRICT,
    canal VARCHAR(20) NOT NULL CHECK (canal IN ('EMAIL', 'WHATSAPP')),
    status VARCHAR(20) NOT NULL CHECK (status IN ('PENDENTE', 'ENVIADO', 'FALHA')),
    tentativas INTEGER NOT NULL DEFAULT 0 CHECK (tentativas >= 0),
    enviado_em TIMESTAMPTZ,
    criado_em TIMESTAMPTZ NOT NULL DEFAULT CURRENT_TIMESTAMP
);

-- Índice composto para busca eficiente da fila de envios pendentes
CREATE INDEX idx_notificacoes_status_criado_em
    ON notificacoes_envio (status, criado_em);

-- Índice na chave estrangeira para acelerar JOINs
CREATE INDEX idx_notificacoes_cliente_id
    ON notificacoes_envio (cliente_id);
```

---

## 4. Erros Comuns e Como Evitá-los

| Erro Comum | Problema | Solução Recomendada |
| :--- | :--- | :--- |
| **Uso de `SELECT *` em consultas de produção** | Transfere colunas desnecessárias (inclusive textos longos ou hashes) pela rede e impede *Index-Only Scans*. | Declarar explicitamente apenas as colunas necessárias para a operação. |
| **Falta de índice em `FOREIGN KEY`** | Causa *Sequential Scan* na tabela filha durante `JOIN` ou verificações de `DELETE`/`UPDATE` na tabela pai. | Criar índice explícito em toda coluna de chave estrangeira. |
| **Armazenar datas sem fuso horário (`TIMESTAMP` vs `TIMESTAMPTZ`)** | Gera ambiguidade em servidores distribuídos ou mudanças de horário. | Armazenar sempre em UTC com suporte a timezone (`TIMESTAMPTZ` no PostgreSQL / ISO-8601 UTC). |
| **Alterar uma migration que já foi executada em equipe** | Quebra o *checksum* de ferramentas como Flyway/Liquibase nos ambientes dos demais desenvolvedores. | Criar uma **nova** migration incremental para corrigir ou evoluir o esquema. |

---

## 5. Referências Oficiais

- **PostgreSQL Official Documentation:** https://www.postgresql.org/docs/current/
- **Use The Index, Luke (Guia de Performance SQL):** https://use-the-index-luke.com/
- **Flyway Documentation:** https://documentation.red-gate.com/fd

