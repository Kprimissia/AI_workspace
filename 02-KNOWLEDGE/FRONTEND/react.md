# Guia Técnico: React (React 18 / 19+) e React Router DOM 7

## 1. Visão Geral e Conceitos Fundamentais

O **React** constrói interfaces de usuário declarativas baseadas em componentes funcionais, fluxo de dados unidirecional (*top-down*) e gerenciamento previsível de estado.

### Conceitos Essenciais
- **Pureza de Componentes:** A função de renderização deve ser pura em relação às suas `props` e `state` — sem causar efeitos colaterais durante o render.
- **Estado Derivado vs. Estado Armazenado:** Se um valor pode ser calculado diretamente a partir das `props` ou do estado existente durante o render, **não** crie um `useState` nem um `useEffect` para sincronizá-lo.
- **Hooks e Regras dos Hooks:** Devem ser chamados apenas no nível superior de componentes funcionais ou *Custom Hooks* (nunca dentro de `if`, loops ou funções aninhadas).
- **React 19 Actions e Form Handling:** Suporte aprimorado a transições assíncronas (`useTransition`, `useActionState`, `useOptimistic`) para estados pendentes e submissão de formulários.

---

## 2. Boas Práticas de Desenvolvimento

1. **Evitar `useEffect` Desnecessários:**
   - Utilize `useEffect` apenas para sincronizar o componente com sistemas externos (APIs de navegador, timers, WebSockets).
   - Ações disparadas pelo usuário (clique em botão, envio de formulário) devem ser tratadas nos **Event Handlers** (`onClick`, `onSubmit`), não via `useEffect`.
2. **Tratar os 4 Estados de Toda Interface Assíncrona:**
   - Todo componente que consome dados da API deve prever explicitamente: **Carregamento (`loading`)**, **Erro (`error`)**, **Vazio (`empty`)** e **Sucesso (`data`)**.
3. **Chaves Estáveis em Listas (`key`):**
   - Utilize sempre identificadores únicos do domínio (`item.id`) na propriedade `key`. Nunca utilize o índice do array (`index`) se a lista puder ser filtrada, reordenada ou sofrer inserções/remoções.
4. **Componentização com Responsabilidade Única:**
   - Separe componentes de apresentação (*UI Components* reutilizáveis) de componentes de página/container que orquestram chamadas de serviço e roteamento.
5. **Proteção de Rotas no React Router DOM 7:**
   - Centralize a verificação de sessão e perfil de acesso em um componente de rota protegida (`<ProtectedRoute />` usando `<Navigate to="/login" replace />` e `<Outlet />`), lembrando que a validação real de segurança sempre ocorre no back-end.

---

## 3. Exemplos Práticos

### 3.1. Componente com Estado Derivado (Sem `useEffect` Redundante) e Estados de UI

```tsx
import { useState, useEffect } from 'react';

export interface NotificacaoItem {
  id: string;
  cliente: string;
  status: 'PENDENTE' | 'ENVIADO' | 'ERRO';
}

interface FilaNotificacoesProps {
  buscarFila: (signal: AbortSignal) => Promise<NotificacaoItem[]>;
}

export function FilaNotificacoes({ buscarFila }: FilaNotificacoesProps) {
  const [itens, setItens] = useState<NotificacaoItem[]>([]);
  const [carregando, setCarregando] = useState<boolean>(true);
  const [erro, setErro] = useState<string | null>(null);
  const [filtroStatus, setFiltroStatus] = useState<string>('TODOS');

  useEffect(() => {
    const controller = new AbortController();
    setCarregando(true);
    setErro(null);

    buscarFila(controller.signal)
      .then((dados) => setItens(dados))
      .catch((err: unknown) => {
        if (err instanceof Error && err.name !== 'AbortError') {
          setErro(err.message);
        }
      })
      .finally(() => setCarregando(false));

    return () => controller.abort();
  }, [buscarFila]);

  // Estado derivado calculado diretamente no render (sem useState/useEffect extra)
  const itensFiltrados =
    filtroStatus === 'TODOS'
      ? itens
      : itens.filter((item) => item.status === filtroStatus);

  if (carregando) {
    return <p role="status">Carregando fila de notificações...</p>;
  }

  if (erro) {
    return <div role="alert">Não foi possível carregar a fila: {erro}</div>;
  }

  return (
    <section aria-labelledby="titulo-fila">
      <h2 id="titulo-fila">Notificações ({itensFiltrados.length})</h2>

      <label htmlFor="filtro-status">Filtrar por status:</label>
      <select
        id="filtro-status"
        value={filtroStatus}
        onChange={(e) => setFiltroStatus(e.target.value)}
      >
        <option value="TODOS">Todos</option>
        <option value="PENDENTE">Pendentes</option>
        <option value="ENVIADO">Enviados</option>
        <option value="ERRO">Com erro</option>
      </select>

      {itensFiltrados.length === 0 ? (
        <p>Nenhuma notificação encontrada para o filtro selecionado.</p>
      ) : (
        <ul>
          {itensFiltrados.map((item) => (
            <li key={item.id}>
              <strong>{item.cliente}</strong> — <span>{item.status}</span>
            </li>
          ))}
        </ul>
      )}
    </section>
  );
}
```

---

## 4. Erros Comuns e Como Evitá-los

| Erro Comum | Problema | Solução Recomendada |
| :--- | :--- | :--- |
| **Sincronizar estado com `useEffect`** | Criar `const [filtrados, setFiltrados] = useState([])` e usar `useEffect` para atualizar quando `itens` ou `filtro` mudam gera renderizações extras e bugs de sincronia. | Calcular `const filtrados = ...` diretamente no corpo do componente (ou com `useMemo` se o cálculo for comprovadamente pesado). |
| **Atualizar estado com base no valor anterior sem função *updater*** | `setContador(contador + 1)` chamado múltiplas vezes usa o valor antigo capturado na *closure*. | Usar a forma funcional: `setContador((atual) => atual + 1)`. |
| **Mutar estado diretamente** | `itens.push(novo); setItens(itens)` não dispara re-render porque a referência do array permanece a mesma. | Criar nova referência: `setItens((atuais) => [...atuais, novo])`. |
| **Definir componentes dentro de outros componentes** | `function Pai() { function Filho() { ... } }` recria a definição de `Filho` a cada render, destruindo o estado e o foco dos inputs. | Declarar todos os componentes no nível do módulo. |

---

## 5. Referências Oficiais

- **React Official Documentation (react.dev):** https://react.dev/
- **You Might Not Need an Effect:** https://react.dev/learn/you-might-not-need-an-effect
- **React Router DOM v7 Documentation:** https://reactrouter.com/

