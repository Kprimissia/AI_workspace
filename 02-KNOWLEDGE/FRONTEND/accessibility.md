# Guia Técnico: Acessibilidade Web (WCAG 2.1 / 2.2 Nível AA)

## 1. Visão Geral e Conceitos Fundamentais

A **Acessibilidade Web (a11y)** garante que qualquer pessoa — incluindo usuários de leitores de tela, navegação exclusiva por teclado, baixa visão, daltonismo ou limitações motoras — consiga perceber, compreender, navegar e interagir com a aplicação.

### Os 4 Princípios da WCAG (POUR)
1. **Perceptível (*Perceivable*):** Informações e componentes da interface devem ser apresentados de forma que os usuários possam percebê-los (textos alternativos, contraste de cores).
2. **Operável (*Operable*):** Toda funcionalidade deve ser operável por teclado, com foco visível e alvos de toque adequados.
3. **Compreensível (*Understandable*):** Navegação consistente, rótulos claros e mensagens de erro que explicam como corrigir o problema.
4. **Robusto (*Robust*):** Código HTML semântico e atributos ARIA válidos para tecnologias assistivas.

---

## 2. Boas Práticas Obrigatórias (Padrão WCAG AA)

1. **Primeira Regra do ARIA:**
   - **Não utilize ARIA se um elemento ou atributo HTML nativo já possui a semântica e o comportamento necessários** (ex.: use `<button>` em vez de `<div role="button" tabIndex={0}>`; use `<dialog>` em vez de divs genéricas).
2. **Contraste de Cores e Independência de Cor:**
   - Texto normal: proporção mínima de contraste de **4.5:1** contra o fundo.
   - Texto grande (`>= 18pt` ou `>= 14pt bold`) e componentes de interface/ícones: mínimo de **3:1**.
   - Nunca use **apenas a cor** (ex.: borda vermelha ou círculo verde) para indicar status ou erro; inclua texto ou ícone com rótulo acessível.
3. **Formulários Acessíveis:**
   - Todo `<input>`, `<select>` e `<textarea>` deve ter um `<label htmlFor="id-do-campo">` explícito (`placeholder` **não** substitui `<label>`).
   - Campos inválidos devem ter `aria-invalid="true"` e apontar para a mensagem de erro via `aria-describedby="id-do-erro"`.
4. **Navegação por Teclado e Foco:**
   - Todos os controles interativos devem ser alcançáveis com `Tab` / `Shift+Tab` em ordem lógica.
   - Áreas de toque/clique devem ter no mínimo `24x24 CSS pixels` (WCAG 2.2 AA) — recomendando-se `44x44px` em telas móveis.
5. **Regiões Dinâmicas (*Live Regions*):**
   - Mensagens assíncronas importantes (alertas de erro, confirmações de envio, status de carregamento) devem usar `role="alert"` (assertivo) ou `role="status"` / `aria-live="polite"`.

---

## 3. Exemplos Práticos

### 3.1. Campo de Formulário Completo com Estado de Erro Acessível

```tsx
interface CampoCpfProps {
  valor: string;
  erro?: string;
  onChange: (novoValor: string) => void;
}

export function CampoCpf({ valor, erro, onChange }: CampoCpfProps) {
  const inputId = 'campo-cpf';
  const dicaId = 'campo-cpf-dica';
  const erroId = 'campo-cpf-erro';

  const descricoes = [dicaId, erro ? erroId : null].filter(Boolean).join(' ');

  return (
    <div className="form-group">
      <label htmlFor={inputId}>
        CPF do Consorciado <span aria-hidden="true">*</span>
      </label>
      <span id={dicaId} className="form-hint">
        Digite apenas os 11 números.
      </span>
      <input
        id={inputId}
        name="cpf"
        type="text"
        inputMode="numeric"
        required
        value={valor}
        onChange={(e) => onChange(e.target.value)}
        aria-invalid={Boolean(erro)}
        aria-describedby={descricoes}
      />
      {erro && (
        <p id={erroId} role="alert" className="form-error">
          {erro}
        </p>
      )}
    </div>
  );
}
```

### 3.2. Botão Somente com Ícone Acessível

```tsx
<button
  type="button"
  aria-label="Reenviar notificação para o cliente"
  onClick={handleReenviar}
>
  <svg aria-hidden="true" focusable="false" width="20" height="20">
    <use href="#icon-send" />
  </svg>
</button>
```

---

## 4. Erros Comuns e Como Evitá-los

| Erro Comum | Problema | Solução Recomendada |
| :--- | :--- | :--- |
| **Botões de ícone sem texto nem `aria-label`** | Leitores de tela anunciam apenas *"botão"* sem explicar a ação. | Adicionar `aria-label="Descrição da ação"` no `<button>` e `aria-hidden="true"` no `<svg>`. |
| **Pular níveis de cabeçalho (`<h1>` direto para `<h4>`)** | Quebra o mapa de navegação estrutural usado por usuários de leitores de tela. | Manter a hierarquia sequencial (`<h1>` → `<h2>` → `<h3>`) e usar CSS para controlar o tamanho visual. |
| **Usar `tabIndex` maior que `0` (`tabIndex={1}`, `tabIndex={2}`)** | Desorganiza a ordem natural de navegação do DOM. | Usar apenas a ordem natural do DOM (`tabIndex={0}` quando necessário ou `tabIndex={-1}` para foco programático). |
| **Imagens informativas sem `alt` ou decorativas com `alt` poluído** | Imagens sem `alt` fazem o leitor ler o nome do arquivo; ícones decorativos com `alt="ícone seta"` geram ruído. | Usar `alt="Descrição clara"` em imagens informativas e `alt=""` (vazio) em imagens puramente decorativas. |

---

## 5. Referências Oficiais

- **W3C WCAG 2.2 Official Specification:** https://www.w3.org/TR/WCAG22/
- **WAI-ARIA Authoring Practices Guide (APG):** https://www.w3.org/WAI/ARIA/apg/
- **MDN Accessibility Guide:** https://developer.mozilla.org/pt-BR/docs/Web/Accessibility

