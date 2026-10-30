# AGENTS.md — AI_Workspace (Configuração Central e Governança de Agentes)

Este diretório (`AI_workspace`) é a biblioteca central de governança, engenharia de contexto, Skills, Workflows, Prompts, Base de Conhecimento (`02-KNOWLEDGE`), Templates (`03-TEMPLATES`) e especificações de projetos (`01-PROJECTS`) para agentes de IA no **Google Antigravity**.

---

## 1. Regras Globais Obrigatórias (Always-On)

Todas as diretrizes definidas em [global-rules.md](00-GLOBAL/RULES/global-rules.md) estão ativas e são obrigatórias em todas as interações neste ambiente:

@[Global Rules](00-GLOBAL/RULES/global-rules.md)

---

## 2. Hierarquia de Precedência, Segurança e Política Global de Git

Ao executar qualquer tarefa, o agente deve respeitar rigorosamente a seguinte ordem de prioridade:

1. **Regras de Segurança, Isolamento de Git e Limites da Plataforma:**
   - Proteção de credenciais e proibição de comandos destrutivos sem autorização explícita.
   - **Autonomia de Git:** Commits locais pequenos e frequentes são permitidos automaticamente no repositório do projeto após executar os **10 passos obrigatórios de verificação** (Seção 8 de `global-rules.md`, usando staging seletivo `git add <arquivo>` e revisão via `git diff --cached --name-only`).
   - **Operações que exigem autorização explícita:** `git push`, `git merge`, `git rebase`, alteração de remotos, exclusão/reescrita de histórico e deploy.
   - **Bloqueio de arquivos externos:** Nenhum arquivo da `AI_workspace` (`AGENTS.md` raiz, `00-GLOBAL/`, `01-PROJECTS/`, `02-KNOWLEDGE/`, `03-TEMPLATES/`, `.agents/`) pode ser enviado aos repositórios dos projetos.
2. **Instruções Específicas do Projeto (`01-PROJECTS/<PROJETO>/AGENTS.md`):** Prevalecem sobre regras globais em definições técnicas, arquitetura e restrições de escopo (como a restrição exclusiva a Front-end no **UniSENAI** e a sequência de atividades 01 a 08 no **FRONTEND-2S2026**).
3. **Regras Globais (`00-GLOBAL/RULES/global-rules.md`):** Padrão de comunicação (Português brasileiro), análise prévia, transparência e qualidade.
4. **Skills (`00-GLOBAL/SKILLS/`), Workflows (`00-GLOBAL/WORKFLOWS/`), Knowledge (`02-KNOWLEDGE/`) e Templates (`03-TEMPLATES/`):** Procedimentos técnicos, referências e modelos acionados conforme a natureza da tarefa.

---

## 3. Matriz de Papéis e Responsabilidades do Agente

O agente deve assumir dinamicamente o papel técnico adequado à solicitação do usuário, consultando as **Skills**, **Workflows**, **Knowledge** e **Templates** listados nas Seções 4, 5 e 6:

| Papel do Agente | Quando Assumir | Skills | Workflows | Knowledge & Templates |
| :--- | :--- | :--- | :--- | :--- |
| **Desenvolvedor Frontend** | Interfaces, componentes, rotas, estado, CSS, responsividade e consumo de APIs. | `frontend-development` | `feature-development`, `accessibility-review`, `api-integration`, `refactoring` | `react.md`, `html-css.md`, `accessibility.md`, `typescript.md`, `javascript.md` |
| **Desenvolvedor Backend** | APIs, regras de negócio no servidor, autenticação, banco e integrações *(Proibido no UniSENAI)*. | `backend-development` | `feature-development`, `api-integration`, `database-management`, `monitoring-logging` | `apis-rest.md`, `databases.md`, `authentication.md`, `java.md`, `python.md` |
| **Analista de Requisitos** | Requisitos funcionais/não funcionais, regras de negócio, análise prévia e critérios de aceite. | `project-management`, `prompt-engineering` | `requirements-analysis`, `project-initialization` | `requirements-specification.md`, `task-plan.md` |
| **Arquiteto de Software** | Avaliação estrutural, inicialização, modelagem de dados, refatoração e desempenho. | `backend-development`, `frontend-development`, `technical-documentation` | `project-initialization`, `refactoring`, `performance-optimization`, `database-management` | `architecture.md`, `clean-code.md`, `adr-template.md` |
| **Especialista em GitHub** | Branches, análise de status/diff, Issues, Pull Requests, Milestones e GitHub Projects. | `github-management` | `team-collaboration`, `release-deployment` | `git-github.md`, `docker.md`, `deployment.md`, `release-deployment-checklist.md` |
| **Revisor de Código** | Auditoria de commits, branches, PRs ou implementações em busca de bugs e regressões. | `code-review` | `code-review`, `security-review` | `clean-code.md`, `security.md`, `code-review-report.md` |
| **Engenheiro de Testes** | Testes unitários, integração, E2E, regressão, lint, typecheck e build. | `testing-validation` | `bug-fix`, `feature-development`, `release-deployment` | `testing.md`, `test-plan.md`, `bug-report.md` |
| **Gerente de Projetos** | Decomposição de tarefas, backlog, sprints, Kanban, priorização e relatórios de progresso. | `project-management`, `github-management` | `requirements-analysis`, `team-collaboration` | `project-plan.md`, `task-plan.md` |
| **Documentador Técnico** | README, guias de setup, arquitetura, referências de API e ADRs. | `technical-documentation` | `documentation` | `api-documentation.md`, `setup-execution-guide.md`, `adr-template.md` |
| **Especialista em Segurança** | Superfície de ataque, vulnerabilidades (OWASP), proteção de dados (LGPD) e incidentes. | `code-review`, `backend-development` | `security-review`, `incident-response` | `security.md`, `authentication.md` |

---

## 4. Catálogo de Skills Reutilizáveis (`00-GLOBAL/SKILLS/`)

Registradas nativamente via [.agents/skills.json](.agents/skills.json) apontando para `00-GLOBAL/SKILLS`:

1. **`frontend-development`**: [00-GLOBAL/SKILLS/frontend-development/SKILL.md](00-GLOBAL/SKILLS/frontend-development/SKILL.md)
2. **`backend-development`**: [00-GLOBAL/SKILLS/backend-development/SKILL.md](00-GLOBAL/SKILLS/backend-development/SKILL.md)
3. **`github-management`**: [00-GLOBAL/SKILLS/github-management/SKILL.md](00-GLOBAL/SKILLS/github-management/SKILL.md)
4. **`code-review`**: [00-GLOBAL/SKILLS/code-review/SKILL.md](00-GLOBAL/SKILLS/code-review/SKILL.md)
5. **`testing-validation`**: [00-GLOBAL/SKILLS/testing-validation/SKILL.md](00-GLOBAL/SKILLS/testing-validation/SKILL.md)
6. **`technical-documentation`**: [00-GLOBAL/SKILLS/technical-documentation/SKILL.md](00-GLOBAL/SKILLS/technical-documentation/SKILL.md)
7. **`project-management`**: [00-GLOBAL/SKILLS/project-management/SKILL.md](00-GLOBAL/SKILLS/project-management/SKILL.md)
8. **`prompt-engineering`**: [00-GLOBAL/SKILLS/prompt-engineering/SKILL.md](00-GLOBAL/SKILLS/prompt-engineering/SKILL.md)

---

## 5. Roteamento de Workflows (`00-GLOBAL/WORKFLOWS/`) e Prompts (`00-GLOBAL/PROMPTS/`)

### Prompts Base (`00-GLOBAL/PROMPTS/`)
- **Análise prévia de tarefa complexa:** [task-analysis.md](00-GLOBAL/PROMPTS/task-analysis.md)
- **Diagnóstico e investigação de bugs/erros:** [bug-fix.md](00-GLOBAL/PROMPTS/bug-fix.md)

### Workflows Operacionais (`00-GLOBAL/WORKFLOWS/`)
- **Nova funcionalidade:** [feature-development.md](00-GLOBAL/WORKFLOWS/feature-development.md) | **Correção de bug:** [bug-fix.md](00-GLOBAL/WORKFLOWS/bug-fix.md)
- **Revisão de código / PR:** [code-review.md](00-GLOBAL/WORKFLOWS/code-review.md) | **Release e deploy:** [release-deployment.md](00-GLOBAL/WORKFLOWS/release-deployment.md)
- **Inicialização de projeto:** [project-initialization.md](00-GLOBAL/WORKFLOWS/project-initialization.md) | **Refatoração:** [refactoring.md](00-GLOBAL/WORKFLOWS/refactoring.md)
- **Documentação:** [documentation.md](00-GLOBAL/WORKFLOWS/documentation.md) | **Requisitos e backlog:** [requirements-analysis.md](00-GLOBAL/WORKFLOWS/requirements-analysis.md)
- **Integração com APIs:** [api-integration.md](00-GLOBAL/WORKFLOWS/api-integration.md) | **Auditoria de segurança:** [security-review.md](00-GLOBAL/WORKFLOWS/security-review.md)
- **Otimização de performance:** [performance-optimization.md](00-GLOBAL/WORKFLOWS/performance-optimization.md) | **Banco de dados:** [database-management.md](00-GLOBAL/WORKFLOWS/database-management.md)
- **Acessibilidade e UX/UI:** [accessibility-review.md](00-GLOBAL/WORKFLOWS/accessibility-review.md) | **Monitoramento e logs:** [monitoring-logging.md](00-GLOBAL/WORKFLOWS/monitoring-logging.md)
- **Resposta a incidentes:** [incident-response.md](00-GLOBAL/WORKFLOWS/incident-response.md) | **Colaboração em equipe:** [team-collaboration.md](00-GLOBAL/WORKFLOWS/team-collaboration.md)

---

## 6. Base de Conhecimento Técnico (`02-KNOWLEDGE/`) e Modelos (`03-TEMPLATES/`)

### 6.1. Base de Conhecimento (`02-KNOWLEDGE/`)
Consultar durante decisões de implementação, revisão ou diagnóstico técnico:
- **PROGRAMMING:** [javascript.md](02-KNOWLEDGE/PROGRAMMING/javascript.md), [typescript.md](02-KNOWLEDGE/PROGRAMMING/typescript.md), [java.md](02-KNOWLEDGE/PROGRAMMING/java.md), [python.md](02-KNOWLEDGE/PROGRAMMING/python.md)
- **FRONTEND:** [react.md](02-KNOWLEDGE/FRONTEND/react.md), [html-css.md](02-KNOWLEDGE/FRONTEND/html-css.md), [accessibility.md](02-KNOWLEDGE/FRONTEND/accessibility.md)
- **BACKEND:** [apis-rest.md](02-KNOWLEDGE/BACKEND/apis-rest.md), [databases.md](02-KNOWLEDGE/BACKEND/databases.md), [authentication.md](02-KNOWLEDGE/BACKEND/authentication.md)
- **DEVOPS:** [git-github.md](02-KNOWLEDGE/DEVOPS/git-github.md), [docker.md](02-KNOWLEDGE/DEVOPS/docker.md), [deployment.md](02-KNOWLEDGE/DEVOPS/deployment.md)
- **SOFTWARE-ENGINEERING:** [clean-code.md](02-KNOWLEDGE/SOFTWARE-ENGINEERING/clean-code.md), [architecture.md](02-KNOWLEDGE/SOFTWARE-ENGINEERING/architecture.md), [security.md](02-KNOWLEDGE/SOFTWARE-ENGINEERING/security.md), [testing.md](02-KNOWLEDGE/SOFTWARE-ENGINEERING/testing.md)

### 6.2. Modelos Reutilizáveis (`03-TEMPLATES/`)
Utilizar como estrutura padrão ao produzir especificações, planos, relatórios ou documentações:
- **Requisitos e Planejamento:** [requirements-specification.md](03-TEMPLATES/requirements-specification.md), [project-plan.md](03-TEMPLATES/project-plan.md), [task-plan.md](03-TEMPLATES/task-plan.md)
- **Arquitetura, APIs e Setup:** [adr-template.md](03-TEMPLATES/adr-template.md), [api-documentation.md](03-TEMPLATES/api-documentation.md), [setup-execution-guide.md](03-TEMPLATES/setup-execution-guide.md)
- **Qualidade, Revisão e Deploy:** [test-plan.md](03-TEMPLATES/test-plan.md), [code-review-report.md](03-TEMPLATES/code-review-report.md), [bug-report.md](03-TEMPLATES/bug-report.md), [release-deployment-checklist.md](03-TEMPLATES/release-deployment-checklist.md)

---

## 7. Contexto Obrigatório dos Projetos (`01-PROJECTS/`)

Sempre que a tarefa envolver um dos projetos abaixo, o agente **DEVE** ler imediatamente o respectivo `AGENTS.md`:

- **ConsorTech ([01-PROJECTS/CONSORTECH/AGENTS.md](01-PROJECTS/CONSORTECH/AGENTS.md)):** Sistema de comunicação e baixa de clientes contemplados em consórcios (`C:\Users\kaiqu\OneDrive\Desktop\SystemEx-PI`). Três repositórios independentes: `front-end` (`SystemX-PI/Front-End.git`), `Back-end` (`SystemX-PI/Back-end.git`) e `documentação-e-arquitetura` (`SystemEx-PI/Documentacao-e-Arquitetura.git`). Proibido criar endpoints fictícios, simular integrações ou commitar binários `bin/*.class`.
- **UniSENAI ([01-PROJECTS/UNISENAI/AGENTS.md](01-PROJECTS/UNISENAI/AGENTS.md)):** **Restrição Crítica Front-end Only** (`C:\Users\kaiqu\OneDrive\Desktop\frontend`, remote `UniSENAI-Sorocaba/plataforma-frontend`). O agente deve atuar **exclusivamente no Front-end**. É estritamente proibido desenvolver funcionalidades de back-end, criar/modificar endpoints, alterar regras de servidor, modificar banco de dados ou criar migrations.
- **FRONTEND-2S2026 ([01-PROJECTS/FRONTEND-2S2026/AGENTS.md](01-PROJECTS/FRONTEND-2S2026/AGENTS.md)):** Atividades `01` a `08` da disciplina de Front-End (`C:\Users\kaiqu\OneDrive\Desktop\Kaique\frontend-2s2026`, remote `Kprimissia/frontend-2s2026.git`). Execução estritamente sequencial (01 a 08) fiel ao material do professor, com commits locais pequenos, frequentes e cronológicos.
