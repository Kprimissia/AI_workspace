# Plano de Projeto — [NOME DO PROJETO]

**Projeto:** `[Nome do Projeto]`  
**Data de Atualização:** `AAAA-MM-DD`  
**Metodologia Adotada:** `[Scrum / Kanban / Iterativo]`  
**Repositórios:** `[Links ou caminhos para Front-end / Back-end]`

---

## 1. Visão Geral do Projeto

- **Objetivo Principal:** `[Qual problema de negócio o projeto resolve]`
- **Público-Alvo:** `[Quem utiliza a solução]`
- **Escopo Geral Autorizado:** `[Ex.: Front-end + Back-end | Exclusivamente Front-end]`

---

## 2. Stack Tecnológica Verificada

| Camada | Tecnologias e Versões | Observações / Configurações |
| :--- | :--- | :--- |
| **Front-end** | `[Ex.: React 19, TypeScript, Vite, React Router DOM 7]` | `[Ex.: Variável VITE_API_URL, proxy /api]` |
| **Back-end** | `[Confirmado no repositório ou A Confirmar]` | `[Porta, framework, autenticação]` |
| **Banco de Dados** | `[Confirmado no repositório ou A Confirmar]` | `[Ferramenta de migrations]` |
| **Qualidade / Testes** | `[Ex.: Oxlint, ESLint, Vitest, JUnit]` | `[Comandos de verificação]` |

---

## 3. Divisão da Equipe e Responsabilidades

| Integrante / Papel | Área de Atuação | Módulos sob Responsabilidade |
| :--- | :--- | :--- |
| `[Nome / Equipe Front-end]` | Front-end | `[Páginas, componentes, integração cliente]` |
| `[Nome / Equipe Back-end]` | Back-end / Banco | `[Endpoints, regras de negócio, persistência]` |

---

## 4. Marcos de Entrega (Milestones)

| Milestone | Objetivo da Entrega | Entregáveis Verificáveis | Status |
| :--- | :--- | :--- | :--- |
| **M1 — Fundação e Autenticação** | `[Estrutura base, login, rotas protegidas]` | `[Telas de login/cadastro e sessão]` | `[Planejado / Em Andamento / Concluído]` |
| **M2 — Módulos Principais** | `[Funcionalidades centrais do domínio]` | `[Painel administrativo, portal, filas]` | `[Planejado / Em Andamento / Concluído]` |
| **M3 — Integrações e Validação** | `[Conexão fim a fim, testes e revisão]` | `[Integração API, suíte de testes, docs]` | `[Planejado / Em Andamento / Concluído]` |

---

## 5. Backlog Priorizado

| ID | Funcionalidade / Épico | Prioridade (`Crítica` / `Alta` / `Média` / `Baixa`) | Dependências | Status |
| :--- | :--- | :--- | :--- | :--- |
| **BL-01** | `[Nome da funcionalidade]` | `Alta` | `[Nenhuma / Endpoint X]` | `[A Fazer]` |
| **BL-02** | `[Nome da funcionalidade]` | `Média` | `[BL-01]` | `[Backlog]` |

---

## 6. Gestão de Riscos e Bloqueios

| Risco / Bloqueio | Impacto | Probabilidade | Estratégia de Mitigação / Ação Necessária | Responsável |
| :--- | :--- | :--- | :--- | :--- |
| `[Ex.: Contrato da API de integração ainda não definido]` | `Alto` | `Média` | `[Documentar contrato esperado e isolar camada de serviço no front-end]` | `[Equipe Back-end / Front-end]` |

---

## 7. Critérios de Pronto (Definition of Done — DoD)

Uma entrega só é considerada **Concluída (`Done`)** quando:
- [ ] O requisito funcional e os critérios de aceitação foram integralmente atendidos.
- [ ] O código respeita a arquitetura do projeto e não introduz regressões.
- [ ] As verificações de `lint`, `typecheck`, `testes` e `build` foram executadas com sucesso.
- [ ] Não há segredos, credenciais ou dados sensíveis expostos.
- [ ] A documentação técnica correspondente foi atualizada.

