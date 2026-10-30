# Plano e Relatório de Testes — [FUNCIONALIDADE / MÓDULO]

**Projeto:** `[Nome do Projeto]`  
**Escopo Avaliado:** `[Arquivos, componentes ou endpoints testados]`  
**Data:** `AAAA-MM-DD`  
**Status Final da Validação:** `[Validado | Parcialmente Validado | Reprovado | Não Executado]`

---

## 1. Estratégia e Ambiente de Testes

- **Níveis de Teste Aplicados:** `[Análise Estática (Lint/Types) | Unitário | Integração | E2E | Manual]`
- **Ferramentas Utilizadas:** `[Ex.: Oxlint / ESLint, TypeScript (tsc), Vitest, Testing Library, Playwright]`
- **Pré-requisitos do Ambiente:** `[Node.js, variáveis de ambiente de teste, mocks de API]`

---

## 2. Matriz de Cenários de Teste

| ID | Categoria (`Feliz` / `Negativo` / `Borda` / `Permissão` / `Regressão`) | Cenário / Condição de Entrada | Resultado Esperado | Status (`Aprovado` / `Reprovado` / `Não Executado`) |
| :--- | :--- | :--- | :--- | :--- |
| **CT-01** | `Caminho Feliz` | Dados válidos submetidos no formulário/endpoint. | Operação concluída e feedback de sucesso exibido. | `[Status]` |
| **CT-02** | `Caminho Negativo` | Campos obrigatórios vazios ou em formato inválido. | Submissão bloqueada e mensagem de erro acessível exibida. | `[Status]` |
| **CT-03** | `Erro de Integração` | API retorna erro `500` ou timeout de rede. | Interface exibe estado de erro amigável e permite nova tentativa. | `[Status]` |
| **CT-04** | `Caso de Borda` | Lista retornada pela API está vazia (`[]`). | Componente exibe estado vazio informativo (*Empty State*). | `[Status]` |
| **CT-05** | `Permissão / Acesso` | Usuário sem permissão tenta acessar rota restrita. | Acesso negado (`403` ou redirecionamento seguro). | `[Status]` |

---

## 3. Comandos Efetivamente Executados e Evidências

| Verificação | Comando Executado | Resultado Obtido (`Código de Saída` / Resumo) |
| :--- | :--- | :--- |
| **Linting** | `[Ex.: npm run lint]` | `[Executado e Aprovado / Reprovado / Não Executado]` |
| **Typecheck** | `[Ex.: npx tsc --noEmit]` | `[Executado e Aprovado / Reprovado / Não Executado]` |
| **Testes Automatizados** | `[Ex.: npm test]` | `[X testes passaram, Y falharam]` |
| **Build de Produção** | `[Ex.: npm run build]` | `[Build concluído com sucesso / Falha]` |

---

## 4. Defeitos Encontrados e Correções Aplicadas

- **Defeito 1:** `[Descrição do erro encontrado, arquivo/linha e causa raiz]`
  - **Correção:** `[O que foi ajustado dentro do escopo autorizado]`

---

## 5. Limitações e Validações Pendentes

- `[Listar claramente quaisquer verificações que não puderam ser executadas — por exemplo, ausência de servidor back-end ativo localmente — e o motivo técnico]`

