# Guia Técnico: JavaScript Moderno (ES6+)

## 1. Visão Geral e Conceitos Fundamentais

O **JavaScript (ECMAScript)** é a linguagem padrão da plataforma web e de ambientes de execução como Node.js, Deno e Bun. Em projetos modernos, prioriza-se o padrão **ES2020+** com módulos nativos (`ESM`), imutabilidade e programação assíncrona baseada em `Promises` (`async`/`await`).

### Conceitos Essenciais
- **Escopo de Bloco (`const` e `let`):** `const` impede a reatribuição da referência (deve ser o padrão); `let` é restrito a variáveis que realmente mudam de valor; `var` não deve ser utilizado devido ao *hoisting* de escopo de função.
- **Event Loop e Assincronicidade:** Operações de I/O não bloqueiam a *main thread*. Microtasks (`Promises`, `queueMicrotask`) têm prioridade sobre Macrotasks (`setTimeout`, `setInterval`, eventos de DOM).
- **Igualdade Estrita (`===` e `!==`):** Evita coerção implícita de tipos.
- **Módulos ES (`import` / `export`):**Permitem *tree-shaking* estático por bundlers como Vite e Rollup.

---

## 2. Boas Práticas de Desenvolvimento

1. **Imutabilidade em Objetos e Arrays:**
   - Prefira métodos não mutáveis (`map`, `filter`, `reduce`, `toSorted`, `toReversed`, `toSpliced`) e *spread operator* (`{ ...obj }`, `[...arr]`) em vez de mutações diretas (`push`, `splice`, `sort`).
2. **Encadeamento Opcional e Coalescência Nula:**
   - Utilize `?.` (*Optional Chaining*) para acessar propriedades aninhadas com segurança.
   - Utilize `??` (*Nullish Coalescing*) em vez de `||` quando `0` ou `""` forem valores válidos.
3. **Tratamento Estruturado de Erros Assíncronos:**
   - Envolva chamadas `await` em blocos `try / catch / finally` e preserve a causa original do erro com `new Error("Mensagem contextual", { cause: err })`.
4. **Concorrência Controlada:**
   - Quando múltiplas requisições assíncronas não dependem umas das outras, execute-as em paralelo com `Promise.all()` ou `Promise.allSettled()`, evitando *waterfalls* sequenciais desnecessários.
5. **Cancelamento de Operações:**
   - Utilize `AbortController` e passe `signal` para chamadas `fetch` e *event listeners* para evitar vazamento de memória e condições de corrida (*race conditions*).

---

## 3. Exemplos Práticos

### 3.1. Requisição HTTP Segura com Timeout e Cancelamento (`AbortController`)

```javascript
export async function fetchJsonWithTimeout(url, options = {}, timeoutMs = 8000) {
  const controller = new AbortController();
  const timeoutId = setTimeout(() => controller.abort(), timeoutMs);

  try {
    const response = await fetch(url, {
      ...options,
      headers: {
        Accept: 'application/json',
        ...options.headers,
      },
      signal: controller.signal,
    });

    if (!response.ok) {
      throw new Error(`Erro HTTP ${response.status}: ${response.statusText}`);
    }

    return await response.json();
  } catch (error) {
    if (error.name === 'AbortError') {
      throw new Error(`Tempo limite de ${timeoutMs}ms excedido para ${url}`, { cause: error });
    }
    throw error;
  } finally {
    clearTimeout(timeoutId);
  }
}
```

### 3.2. Processamento Imutável e Paralelismo com `Promise.allSettled`

```javascript
export async function sincronizarNotificacoes(ids, enviarNotificacao) {
  const resultados = await Promise.allSettled(
    ids.map((id) => enviarNotificacao(id))
  );

  return resultados.reduce(
    (acc, resultado, index) => {
      if (resultado.status === 'fulfilled') {
        return { ...acc, enviados: [...acc.enviados, ids[index]] };
      }
      return {
        ...acc,
        falhas: [...acc.falhas, { id: ids[index], motivo: resultado.reason?.message }],
      };
    },
    { enviados: [], falhas: [] }
  );
}
```

---

## 4. Erros Comuns e Como Evitá-los

| Erro Comum | Problema | Solução Recomendada |
| :--- | :--- | :--- |
| **`await` dentro de loop `forEach`** | `Array.prototype.forEach` não aguarda `Promises`; erros não são capturados pelo `try/catch` externo. | Usar `for (const item of items)` para execução sequencial ou `await Promise.all(items.map(...))` para paralelo. |
| **Uso de `||` para valor padrão numérico/texto** | `const qtd = input || 10` sobrescreve `0` por `10` (pois `0` é *falsy*). | Usar `const qtd = input ?? 10` (apenas `null` ou `undefined` acionam o fallback). |
| **Mutação de array com `.sort()`** | `array.sort()` altera o array original in-place, causando efeitos colaterais no estado (ex.: React). | Usar `array.toSorted(comparador)` (ES2023) ou `[...array].sort(comparador)`. |
| **Comparação imprecisa de ponto flutuante** | `0.1 + 0.2 === 0.3` resulta em `false` (IEEE 754). | Trabalhar com centavos inteiros para valores monetários e usar `Intl.NumberFormat('pt-BR', { style: 'currency', currency: 'BRL' })` na exibição. |
| **Esquecer `return` ou `await` em `try/catch`** | Retornar `Promise` sem `await` dentro de um bloco `try` impede que o `catch` local capture rejeições. | Usar `return await operacaoAssincrona()` quando estiver dentro de um bloco `try/catch`. |

---

## 5. Referências Oficiais

- **MDN Web Docs — JavaScript:** https://developer.mozilla.org/pt-BR/docs/Web/JavaScript
- **ECMA-262 Specification (TC39):** https://tc39.es/ecma262/
- **JavaScript.info (Guia Moderno):** https://javascript.info/

