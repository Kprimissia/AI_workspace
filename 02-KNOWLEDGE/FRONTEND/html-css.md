# Guia Técnico: HTML5 Semântico e CSS Moderno

## 1. Visão Geral e Conceitos Fundamentais

A base de qualquer aplicação front-end robusta, responsiva e acessível reside no uso correto de **HTML5 Semântico** combinado com **CSS Moderno** (Custom Properties, Flexbox, CSS Grid, unidades relativas e *Container/Media Queries*).

### Conceitos Essenciais
- **HTML Semântico:** Elementos como `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<dialog>` e `<footer>` comunicam significado estrutural ao navegador, motores de busca e leitores de tela.
- **Box Model Padronizado:** `box-sizing: border-box` garante que `padding` e `border` sejam incluídos na largura/altura declarada do elemento.
- **Design Tokens via CSS Custom Properties (`--var`):** Centralizam cores, espaçamentos, tipografia, sombras e *border-radius* no `:root`, facilitando manutenção e consistência visual.
- **Layout Bidimensional vs. Unidimensional:**
  - **CSS Grid:** Ideal para a estrutura macro da página e grades bidimensionais (linhas e colunas).
  - **Flexbox:** Ideal para alinhamento e distribuição de elementos em um único eixo (barras de navegação, botões, cabeçalhos de cards).

---

## 2. Boas Práticas de Desenvolvimento

1. **Usar o Elemento Nativo Correto:**
   - Ações que executam lógica na mesma tela (`abrir modal`, `enviar formulário`, `filtrar`) devem usar `<button type="button">` ou `<button type="submit">`.
   - Navegações que mudam de URL/rota devem usar `<a href="...">` (ou `<Link to="...">` do React Router).
   - Nunca use `<div onClick={...}>` no lugar de um `<button>`.
2. **Unidades Relativas e Tipografia Fluida:**
   - Utilize `rem` para tamanhos de fonte e espaçamentos (respeitando a preferência de zoom/fonte do usuário no navegador).
   - Utilize `clamp(min, ideal, max)` para tipografia fluida e `min()` / `max()` para larguras de containers.
3. **Responsividade *Mobile-First* e Grades Automáticas:**
   - Com CSS Grid, `grid-template-columns: repeat(auto-fit, minmax(min(100%, 280px), 1fr))` cria layouts responsivos sem necessidade de dezenas de `@media` queries.
4. **Prevenção de Rolagem Horizontal Acidental (`Overflow`):**
   - Defina `max-width: 100%; height: auto; display: block;` para imagens e mídias, e envolva tabelas largas em um container com `overflow-x: auto`.

---

## 3. Exemplos Práticos

### 3.1. Sistema de Design Tokens e Reset Base em CSS

```css
:root {
  /* Paleta semântica */
  --color-bg-primary: #f8fafc;
  --color-surface: #ffffff;
  --color-text-primary: #0f172a;
  --color-text-secondary: #475569;
  --color-brand: #0284c7;
  --color-brand-hover: #0369a1;
  --color-danger: #dc2626;
  --color-border: #cbd5e1;

  /* Espaçamento e bordas */
  --space-xs: 0.25rem;
  --space-sm: 0.5rem;
  --space-md: 1rem;
  --space-lg: 1.5rem;
  --space-xl: 2rem;
  --radius-md: 0.5rem;
}

*,
*::before,
*::after {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: system-ui, -apple-system, sans-serif;
  color: var(--color-text-primary);
  background-color: var(--color-bg-primary);
  line-height: 1.5;
}
```

### 3.2. Grid Responsivo de Cards e Formulário Semântico

```css
.cards-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(100%, 18rem), 1fr));
  gap: var(--space-lg);
  padding: var(--space-lg);
}

.card {
  background: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-md);
  padding: var(--space-lg);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
```

---

## 4. Erros Comuns e Como Evitá-los

| Erro Comum | Problema | Solução Recomendada |
| :--- | :--- | :--- |
| **`<button>` dentro de `<form>` sem atributo `type`** | Por padrão no HTML, `<button>` sem `type` assume `type="submit"`, disparando o envio do formulário acidentalmente ao clicar. | Declarar sempre `type="button"` para botões auxiliares e `type="submit"` apenas para o botão de envio. |
| **Remover `outline: none` no `:focus`** | Impede que usuários que navegam por teclado saibam qual elemento está focado. | Usar `:focus-visible` com um contorno nítido (`outline: 2px solid var(--color-brand); outline-offset: 2px;`). |
| **Usar `100vw` com barra de rolagem vertical** | `100vw` inclui a largura da barra de rolagem no Windows, gerando rolagem horizontal indesejada. | Usar `width: 100%` no container de nível de bloco. |
| **Alturas fixas (`height: 300px`) em containers de texto** | Quando o texto cresce ou o usuário aumenta a fonte do sistema, o conteúdo vaza para fora do card. | Usar `min-height` em vez de `height` fixa. |

---

## 5. Referências Oficiais

- **MDN Web Docs — HTML:** https://developer.mozilla.org/pt-BR/docs/Web/HTML
- **MDN Web Docs — CSS:** https://developer.mozilla.org/pt-BR/docs/Web/CSS
- **web.dev — Learn CSS & HTML (Google):** https://web.dev/learn/css

