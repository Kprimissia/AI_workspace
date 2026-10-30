# Relatório de Diagnóstico e Correção de Bug — [TÍTULO DO DEFEITO]

**Projeto:** `[Nome do Projeto]`  
**Módulo / Área (`Front-end` / `Back-end`):** `[Área afetada]`  
**Severidade:** `[Crítica | Alta | Média | Baixa]`  
**Status Final:** `[Resolvido | Parcialmente Resolvido | Não Resolvido / Bloqueado por Escopo]`

---

## 1. Descrição do Problema

- **Comportamento Incorreto Observado (Sintoma):** `[O que está acontecendo de errado, incluindo mensagens de erro ou logs]`
- **Comportamento Esperado:** `[O que o sistema deveria fazer segundo os requisitos]`
- **Passos para Reproduzir:**
  1. `[Passo 1]`
  2. `[Passo 2]`
  3. `[Resultado observado]`
- **Reprodutibilidade:** `[Reproduzido e confirmado | Não pôde ser reproduzido localmente (motivo documentado)]`

---

## 2. Investigação e Causa Raiz

- **Arquivos e Fluxos Inspecionados:** `[Lista de arquivos analisados]`
- **Causa Raiz Identificada:**
  `[Explicação técnica exata do motivo real que origina o defeito, diferenciando o sintoma visível da causa subjacente]`
- **Impacto em Outras Funcionalidades:** `[Quais telas, componentes ou serviços compartilhavam esse fluxo]`

---

## 3. Correção Implementada

- **Estratégia Adotada:** `[Descrição da menor alteração segura capaz de corrigir a causa raiz sem efeitos colaterais]`
- **Arquivos Modificados:**
  - `[caminho/do/arquivo1]` — `[resumo da alteração]`
  - `[caminho/do/arquivo2]` — `[resumo da alteração]`

*(Se a causa raiz estiver fora do escopo autorizado do projeto — ex.: erro no Back-end trabalhando no UniSENAI — descrever aqui a dependência técnica encaminhada para a equipe responsável e o tratamento de erro aplicado no Front-end).*

---

## 4. Validação e Testes de Regressão

| Verificação | Comando / Teste Executado | Resultado |
| :--- | :--- | :--- |
| **Teste do Cenário Original** | `[Teste que reproduz o bug]` | `[Aprovado — erro corrigido]` |
| **Testes de Regressão** | `[Suíte de testes relacionada]` | `[Aprovado / Não Executado]` |
| **Lint & Typecheck** | `[Comandos executados]` | `[Aprovado / Não Executado]` |
| **Build** | `[Comando executado]` | `[Aprovado / Não Executado]` |

---

## 5. Riscos Residuais e Pendências

- `[Informar qualquer limitação de validação, dependência externa ou recomendação preventiva]`

