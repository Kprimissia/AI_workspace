# Guia Técnico: Testes de Software e Validação de Qualidade

## 1. Visão Geral e Conceitos Fundamentais

Testes automatizados e verificações estáticas garantem que o software atende aos requisitos especificados e protegem o projeto contra regressões quando novas alterações são realizadas.

### A Pirâmide de Testes e Verificações Estáticas
1. **Análise Estática (Base Contínua):** Verificação de tipos (`tsc --noEmit`, `mypy`) e Linting (`oxlint`, `eslint`, `ruff`). Detecta erros de sintaxe, contrato e código morto instantaneamente.
2. **Testes Unitários (Rápidos e Isolados):** Testam funções puras, regras de negócio, validadores, formatadores e componentes isolados (ex.: `Vitest`, `Jest`, `JUnit 5`, `pytest`).
3. **Testes de Integração:** Verificam a comunicação real entre módulos — como um componente React interagindo com um serviço (com mock na fronteira de rede via MSW) ou um Controller conversando com o Service e um banco de teste.
4. **Testes End-to-End (E2E):** Validam os fluxos críticos completos do usuário no navegador (ex.: `Playwright`, `Cypress`), como login, preenchimento de formulário e confirmação de operação.

---

## 2. Boas Práticas de Escrita de Testes

1. **Padrão AAA (*Arrange, Act, Assert*):**
   - **Arrange (Preparar):** Configurar os dados de entrada, estado inicial e mocks necessários.
   - **Act (Agir):** Executar a função, requisição ou interação do usuário que está sendo testada.
   - **Assert (Verificar):** Conferir se o resultado observável (retorno, estado na tela, status HTTP) corresponde ao esperado.
2. **Testar Comportamento Observável, Não Detalhes de Implementação:**
   - No Front-end (Testing Library), busque elementos pelo papel acessível e rótulo (`getByRole('button', { name: /enviar/i })`, `getByLabelText(/e-mail/i)`), e não por classes CSS internas ou nomes de variáveis de estado.
3. **Cobrir os 4 Cenários Essenciais:**
   - **Caminho Feliz (*Happy Path*):** Entrada válida gerando o resultado esperado.
   - **Caminho Negativo (*Error Path*):** Entradas inválidas, erro `401`/`422`/`500` da API ou falha de rede.
   - **Casos de Borda (*Boundary / Edge Cases*):** Listas vazias (`[]`), valores limites (`0`, tamanho máximo de texto), cliques duplos rápidos.
   - **Regressão:** Sempre que corrigir um bug, crie um teste que reproduza o defeito original e comprove que foi corrigido.
4. **Independência e Determinismo:**
   - Um teste nunca deve depender da ordem de execução de outro teste, do relógio real do sistema sem controle ou de serviços externos de produção.

---

## 3. Exemplos Práticos

### 3.1. Teste Unitário de Regra de Negócio com Padrão AAA (Vitest / Jest)

```typescript
import { describe, it, expect } from 'vitest';
import { podeReenviarNotificacao } from './notificacaoRules';

describe('podeReenviarNotificacao', () => {
  it('deve permitir o reenvio quando o status for FALHA e tentativas forem menores que 3', () => {
    // Arrange
    const notificacao = { status: 'FALHA' as const, tentativas: 2 };

    // Act
    const resultado = podeReenviarNotificacao(notificacao);

    // Assert
    expect(resultado).toBe(true);
  });

  it('deve bloquear o reenvio quando o limite de 3 tentativas for atingido', () => {
    // Arrange
    const notificacao = { status: 'FALHA' as const, tentativas: 3 };

    // Act
    const resultado = podeReenviarNotificacao(notificacao);

    // Assert
    expect(resultado).toBe(false);
  });
});
```

---

## 4. Erros Comuns e Como Evitá-los

| Erro Comum | Problema | Solução Recomendada |
| :--- | :--- | :--- |
| **Testes sem asserção real (`expect(true).toBe(true)`)** | Inflam artificialmente a cobertura de linhas sem testar se o sistema funciona. | Verificar sempre o resultado real retornado ou renderizado. |
| **Mockar o próprio módulo que está sendo testado** | O teste valida apenas o mock configurado pelo desenvolvedor, não o código real. | Mockar apenas dependências externas (rede, relógio, serviços de terceiros) nas fronteiras. |
| **Afirmar que testes passaram sem executá-los** | Viola a confiabilidade técnica do projeto e oculta quebras de build. | Executar efetivamente os comandos (`npm test`, `npm run lint`, `npm run build`) e relatar a saída real. |
| **Alterar o teste para passar quando a implementação tem um bug** | Esconde o defeito em vez de corrigi-lo. | Investigar a causa raiz da falha antes de decidir se o erro está no código ou no teste desatualizado. |

---

## 5. Referências Oficiais

- **Vitest Documentation:** https://vitest.dev/
- **Testing Library (React / DOM):** https://testing-library.com/docs/
- **Playwright Documentation:** https://playwright.dev/docs/intro
- **pytest Documentation:** https://docs.pytest.org/

