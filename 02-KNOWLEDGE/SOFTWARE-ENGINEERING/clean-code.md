# Guia Técnico: Clean Code, Legibilidade e Manutenibilidade

## 1. Visão Geral e Conceitos Fundamentais

**Código Limpo (*Clean Code*)** é aquele que pode ser lido, compreendido, testado e modificado por outros desenvolvedores da equipe com o mínimo de esforço cognitivo e risco de regressão.

### Princípios Fundamentais
- **KISS (*Keep It Simple, Stupid*):** Prefira a solução mais simples e direta que resolva o problema real. Evite complexidade acidental.
- **YAGNI (*You Aren't Gonna Need It*):** Não construa abstrações genéricas, configurações ou parâmetros para requisitos hipotéticos que não foram solicitados.
- **DRY (*Don't Repeat Yourself*) com Critério:** Evite duplicar regras de negócio e contratos de domínio, mas não force o acoplamento de dois trechos de código que apenas parecem semelhantes por coincidência.
- **Boy Scout Rule:** Deixe o trecho de código trabalhado mais organizado do que o encontrou, **sem** realizar refatorações fora do escopo autorizado da tarefa.

---

## 2. Boas Práticas de Escrita de Código

1. **Nomenclatura Reveladora de Intenção:**
   - Variáveis e propriedades devem usar substantivos claros (`clientesContemplados`, `limiteTentativasEnvio`, não `lista`, `dados`, `temp` ou `x`).
   - Booleanos devem soar como perguntas afirmativas (`isAutenticado`, `possuiPermissaoAdmin`, `podeReenviarNotificacao`).
   - Funções e métodos devem começar com verbos que descrevam exatamente o que fazem (`calcularValorParcela`, `buscarNotificacoesPendentes`, `validarFormatoCpf`).
2. **Funções Pequenas e com Responsabilidade Única:**
   - Uma função deve fazer apenas uma coisa e em um único nível de abstração.
   - Evite funções com mais de 3 parâmetros posicionais; agrupe parâmetros relacionados em um objeto tipado (*Parameter Object*).
   - Evite parâmetros booleanos (*Flag Arguments* como `processarCliente(cliente, true, false)`), dividindo em funções de intenção explícita.
3. **Cláusulas de Guarda (*Early Return*):**
   - Valide casos de erro, nulos ou condições de saída no início da função e retorne imediatamente, evitando aninhamento profundo de `if / else / if / else` (*Arrow Anti-Pattern*).
4. **Eliminação de *Magic Numbers* e *Magic Strings*:**
   - Extraia números e literais com significado de domínio para constantes nomeadas (`const MAX_TENTATIVAS_REENVIO = 3;`).
5. **Comentários Úteis vs. Ruído:**
   - O código deve explicar **o que** está sendo feito; comentários devem existir apenas para explicar **o porquê** de uma decisão técnica não óbvia, limitação de API externa ou regra de negócio específica. Nunca deixe código comentado morto (*dead code*).

---

## 3. Exemplos Práticos

### 3.1. Substituição de Aninhamento Profundo por *Guard Clauses*

```typescript
// ❌ RUIM: Aninhamento profundo, nomes vagos e números mágicos
function proc(u: User | null, n: Notification | null): string {
  if (u !== null) {
    if (u.active) {
      if (n !== null) {
        if (n.tries < 3) {
          return enviar(u, n);
        } else {
          return 'Limite excedido';
        }
      } else {
        return 'Sem notificação';
      }
    } else {
      return 'Usuário inativo';
    }
  }
  return 'Usuário inválido';
}

// ✅ BOM: Guard Clauses, constantes nomeadas e fluxo linear claro
const LIMITE_MAXIMO_TENTATIVAS = 3;

export function processarEnvioNotificacao(
  usuario: User | null,
  notificacao: Notification | null
): string {
  if (!usuario) return 'Usuário inválido';
  if (!usuario.active) return 'Usuário inativo';
  if (!notificacao) return 'Sem notificação';
  if (notificacao.tries >= LIMITE_MAXIMO_TENTATIVAS) return 'Limite excedido';

  return enviar(usuario, notificacao);
}
```

---

## 4. Code Smells Comuns e Como Corrigi-los

| Code Smell | Sintoma | Refatoração Recomendada |
| :--- | :--- | :--- |
| **Long Function / God Component** | Função ou componente React com centenas de linhas misturando estado, chamadas HTTP, formatação e JSX. | Extrair funções puras de formatação/validação, *custom hooks* de dados e subcomponentes menores. |
| **Primitive Obsession** | Passar CPF, e-mail, moeda ou status como `string` ou `number` solto sem validação consistente. | Centralizar tipos, validadores ou objetos de valor (*Value Objects*). |
| **Swallowing Exceptions (`catch (e) {}`)** | Capturar um erro e ignorá-lo silenciosamente, fazendo o sistema falhar mais adiante sem rastro. | Tratar o erro adequadamente, exibir feedback ao usuário ou relançar com contexto. |
| **Feature Envy** | Um módulo acessa repetidamente dados internos de outro módulo para calcular algo que deveria pertencer ao próprio módulo de origem. | Mover a função de cálculo para o módulo dono dos dados. |

---

## 5. Referências Técnicas

- **Refactoring.Guru (Catálogo de Code Smells e Refatorações):** https://refactoring.guru/pt-br/refactoring
- **Google TypeScript / Java / Python Style Guides:** https://google.github.io/styleguide/

