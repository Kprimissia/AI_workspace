# Relatório de Code Review — [ESCOPO / PR / BRANCH]

**Projeto:** `[Nome do Projeto]`  
**Branch / PR Avaliado:** `[branch-origem -> branch-destino]`  
**Data:** `AAAA-MM-DD`  
**Recomendação Final:** `[Aprovado | Aprovado com Sugestões | Alterações Solicitadas | Inconclusivo]`

---

## 1. Resumo Executivo e Escopo

- **Objetivo da Alteração Revisada:** `[Descrição concisa do que a mudança implementa ou corrige]`
- **Arquivos Inspecionados:**
  - `[caminho/do/arquivo1]`
  - `[caminho/do/arquivo2]`
- **Conformidade com `AGENTS.md`:** `[Confirmar se as restrições de escopo e arquitetura do projeto foram respeitadas]`

---

## 2. Achados da Revisão (Ordenados por Severidade)

> Classificação: **`CRITICAL`** (risco grave de segurança/perda de dados/quebra total), **`HIGH`** (defeito funcional importante/regressão), **`MEDIUM`** (problema localizado de confiabilidade/manutenção), **`LOW`** (melhoria pontual), **`INFO`** (observação não bloqueante).

### [ACHADO-01] `[Título Objetivo do Problema]`
- **Severidade:** `[CRITICAL | HIGH | MEDIUM | LOW | INFO]`
- **Localização:** `[caminho/do/arquivo#L10-L25]`
- **Problema:** `[Explicação técnica clara do defeito ou risco]`
- **Impacto:** `[O que acontece se o código for integrado sem correção]`
- **Evidência:**
  ```ts
  // Trecho relevante analisado
  ```
- **Recomendação de Correção:** `[Proposta prática e direta para corrigir]`

*(Caso nenhum problema seja identificado no escopo analisado, registrar explicitamente: "Nenhum achado bloqueante foi identificado no escopo revisado.")*

---

## 3. Verificações Técnicas Executadas

| Verificação | Comando / Método | Status |
| :--- | :--- | :--- |
| **Inspeção de Diff (`git diff`)** | Análise estática das alterações | `[Concluído]` |
| **Lint & Typecheck** | `[Comando executado ou Não executado]` | `[Resultado]` |
| **Testes Automatizados** | `[Comando executado ou Não executado]` | `[Resultado]` |
| **Build** | `[Comando executado ou Não executado]` | `[Resultado]` |

---

## 4. Pontos Positivos Observados

- `[Destacar boas decisões de arquitetura, tipagem, acessibilidade ou cobertura de testes presentes na alteração]`

---

## 5. Riscos, Limitações e Próximos Passos

- **Limitações da Revisão:** `[Indicar se a revisão foi apenas estática ou se houve execução completa]`
- **Ações Prioritárias antes da Integração:**
  1. `[Correção obrigatória 1]`
  2. `[Correção obrigatória 2]`

