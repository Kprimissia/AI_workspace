# Especificação de Requisitos — [NOME DA FUNCIONALIDADE / MÓDULO]

**Projeto:** `[Nome do Projeto]`  
**Data:** `AAAA-MM-DD`  
**Responsável / Autor:** `[Nome ou Equipe]`  
**Status:** `[Rascunho | Em Revisão | Aprovado | Implementado]`

---

## 1. Contexto e Objetivo

- **Problema ou Necessidade:** `[Descreva o problema real que precisa ser resolvido]`
- **Objetivo da Funcionalidade:** `[Descreva o resultado esperado para o usuário e para o negócio]`
- **Público-Alvo / Perfis de Usuário:** `[Ex.: Administrador, Funcionário, Cliente Contemplado]`

---

## 2. Escopo

### 2.1. O que está incluído no escopo
- `[Item 1 incluído]`
- `[Item 2 incluído]`

### 2.2. O que está fora do escopo
- `[Item 1 explicitamente excluído desta entrega]`
- `[Item 2 explicitamente excluído]`

---

## 3. Requisitos Funcionais (RF)

| ID | Descrição do Requisito | Prioridade (`Must` / `Should` / `Could`) | Status (`Confirmado` / `Hipótese`) |
| :--- | :--- | :--- | :--- |
| **RF-01** | O sistema deve permitir `[ação ou comportamento observável]`. | `Must` | `Confirmado` |
| **RF-02** | O sistema deve validar `[condição de entrada]` antes de `[operação]`. | `Must` | `Confirmado` |
| **RF-03** | O sistema deve exibir `[feedback visual / mensagem]` quando `[evento]`. | `Should` | `Confirmado` |

---

## 4. Requisitos Não Funcionais (RNF)

| ID | Categoria | Descrição e Critério Técnico |
| :--- | :--- | :--- |
| **RNF-01** | **Segurança** | `[Ex.: Autenticação obrigatória via token; validação de permissão no servidor]` |
| **RNF-02** | **Usabilidade / Acessibilidade** | `[Ex.: Conformidade WCAG AA, navegação por teclado, estados de loading/erro/vazio]` |
| **RNF-03** | **Responsividade** | `[Ex.: Layout compatível com dispositivos móveis (320px+) e desktop]` |
| **RNF-04** | **Desempenho** | `[Ex.: Paginação de listagens acima de 20 registros; timeout de requisição configurado]` |

---

## 5. Regras de Negócio (RN)

- **RN-01:** `[Condição específica do domínio — ex.: Apenas clientes com status CONTEMPLADO podem receber notificação de baixa]`
- **RN-02:** `[Exceção ou restrição — ex.: Limite máximo de 3 tentativas de reenvio automático]`

---

## 6. Dependências e Integrações

- **Dependências de Front-end:** `[Componentes, rotas ou estados compartilhados]`
- **Dependências de Back-end / API:** `[Endpoints necessários, métodos HTTP e contratos JSON]`
- **Dependências de Banco de Dados:** `[Tabelas, colunas ou migrations necessárias]`
- **Serviços Externos:** `[Ex.: API do Gmail, WhatsApp, provedor de autenticação]`

---

## 7. Critérios de Aceitação (Verificáveis)

- [ ] **CA-01 (Cenário de Sucesso):** Dado que `[contexto]`, quando `[ação]`, então `[resultado esperado]`.
- [ ] **CA-02 (Cenário de Validação/Erro):** Dado que `[dados inválidos ou falha da API]`, quando `[ação]`, então `[mensagem de erro clara sem quebrar a tela]`.
- [ ] **CA-03 (Permissões e Segurança):** Dado um usuário com perfil `[perfil sem permissão]`, quando tentar acessar `[recurso]`, então o acesso deve ser bloqueado (`403` / redirecionamento).

---

## 8. Riscos e Dúvidas em Aberto

### 8.1. Riscos Identificados
- **[Alto / Médio / Baixo]:** `[Descrição do risco]` → **Mitigação:** `[Ação preventiva]`

### 8.2. Dúvidas Pendentes de Confirmação
1. `[Pergunta objetiva que depende de definição da equipe ou cliente]`

