# Guia Técnico: TypeScript

## 1. Visão Geral e Conceitos Fundamentais

O **TypeScript** adiciona tipagem estática estrutural ao JavaScript, permitindo detectar erros de contrato, propriedades inexistentes e estados inválidos em tempo de compilação (`tsc`).

### Conceitos Essenciais
- **Modo Estrito (`"strict": true`):** Habilita `strictNullChecks`, `noImplicitAny`, `strictFunctionTypes` e `useUnknownInCatchVariables`. É indispensável para segurança de tipos real.
- **Tipagem Estrutural (*Duck Typing*):** A compatibilidade entre tipos baseia-se na estrutura de suas propriedades, não apenas no nome da interface ou classe.
- **Unions Discriminadas (*Discriminated Unions*):** Modelam estados mutuamente exclusivos usando uma propriedade literal comum (ex.: `status: 'idle' | 'loading' | 'success' | 'error'`).
- **`unknown` vs. `any`:** `any` desativa o verificador de tipos; `unknown` é o tipo seguro que exige *type narrowing* (estreitamento de tipo) antes do uso.

---

## 2. Boas Práticas de Desenvolvimento

1. **Proibir `any` Explícito:**
   - Utilize `unknown` para dados externos (respostas de API não validadas, erros em `catch`, `JSON.parse`) e aplique *Type Guards* para estreitar o tipo.
2. **Modelar Estados Impossíveis como Impossíveis:**
   - Substitua objetos cheios de propriedades booleanas opcionais (`isLoading?: boolean; isError?: boolean; data?: T`) por *Discriminated Unions*.
3. **Usar `Utility Types` Nativos:**
   - Aproveite `Partial<T>`, `Required<T>`, `Pick<T, K>`, `Omit<T, K>`, `Record<K, T>`, `Readonly<T>` e `ReturnType<T>` para evitar duplicação de contratos.
4. **Importações de Tipo Explícitas:**
   - Use `import type { Usuario } from './types'` (compatível com `verbatimModuleSyntax`), garantindo que tipos sejam removidos com segurança no bundle final.
5. **Inferência Inteligente + Contratos Explícitos nas Fronteiras:**
   - Deixe o TypeScript inferir variáveis locais simples, mas declare explicitamente os tipos de parâmetros e retornos de funções públicas, serviços de API e *props* de componentes.

---

## 3. Exemplos Práticos

### 3.1. União Discriminada para Estados de Requisição

```typescript
export type AsyncState<T> =
  | { status: 'idle' }
  | { status: 'loading' }
  | { status: 'success'; data: T }
  | { status: 'error'; errorMessage: string };

export function renderizarResumo<T>(
  state: AsyncState<T>,
  formatar: (item: T) => string
): string {
  switch (state.status) {
    case 'idle':
      return 'Aguardando consulta.';
    case 'loading':
      return 'Carregando dados...';
    case 'success':
      // O TypeScript garante que `state.data` existe aqui
      return formatar(state.data);
    case 'error':
      // O TypeScript garante que `state.errorMessage` existe aqui
      return `Falha: ${state.errorMessage}`;
  }
}
```

### 3.2. Type Guard Seguro para Dados de API (`unknown`)

```typescript
export interface ClienteContemplado {
  id: string;
  nome: string;
  cota: number;
  email: string;
}

export function isClienteContemplado(valor: unknown): valor is ClienteContemplado {
  if (typeof valor !== 'object' || valor === null) {
    return false;
  }
  const registro = valor as Record<string, unknown>;
  return (
    typeof registro.id === 'string' &&
    typeof registro.nome === 'string' &&
    typeof registro.cota === 'number' &&
    typeof registro.email === 'string'
  );
}
```

---

## 4. Erros Comuns e Como Evitá-los

| Erro Comum | Problema | Solução Recomendada |
| :--- | :--- | :--- |
| **Abuso de *Type Assertion* (`as Tipo`)** | ` (await res.json()) as Usuario` mente para o compilador se o back-end mudar o formato da resposta, causando `TypeError` em runtime. | Validar o formato em runtime (Type Guard ou bibliotecas como Zod) quando houver risco de divergência de contrato. |
| **Operador Non-Null Assertion (`!`)** | `usuario!.endereco!.rua` silencia o aviso de `null`/`undefined` e quebra em execução. | Utilizar `usuario?.endereco?.rua ?? 'Endereço não informado'` ou validação explícita. |
| **Enums numéricos padrão (`enum Status { Ativo }`)** | Enums numéricos geram mapeamento reverso em JS e permitem atribuição de números arbitrários em algumas versões. | Preferir *Union Types* de literais (`type Status = 'ATIVO' | 'INATIVO'`) ou objetos `as const`. |
| **Usar `Function` ou `Object` genérico** | Tipos excessivamente abertos que não verificam argumentos nem retorno. | Usar assinaturas explícitas `(...args: Params) => Retorno` ou `Record<string, unknown>`. |

---

## 5. Referências Oficiais

- **TypeScript Documentation & Handbook:** https://www.typescriptlang.org/docs/
- **TSConfig Reference:** https://www.typescriptlang.org/tsconfig
- **TypeScript Deep Dive:** https://basarat.gitbook.io/typescript/

