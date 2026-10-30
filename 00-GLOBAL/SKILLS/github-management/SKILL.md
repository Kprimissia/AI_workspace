---
name: github-management
description: Gerencia e organiza atividades de desenvolvimento com Git e GitHub. Utilize esta skill para analisar repositórios, branches, commits, Issues, Pull Requests, GitHub Projects, milestones, documentação e fluxos de colaboração em equipe.
---

# GitHub Management

## 1. Objetivo

Definir procedimentos para auxiliar no gerenciamento de repositórios, controle de versão e organização de projetos utilizando Git e GitHub.

O objetivo é manter o trabalho organizado, rastreável, seguro e alinhado ao fluxo de desenvolvimento da equipe.

## 2. Escopo

Esta Skill abrange:

- Git e controle de versão.
- Repositórios GitHub.
- Branches.
- Commits.
- Issues.
- Pull Requests.
- GitHub Projects.
- Milestones.
- Labels.
- Code Review.
- Organização de tarefas.
- Documentação de repositórios.
- Colaboração entre integrantes.

## 3. Análise inicial do repositório

Antes de realizar qualquer operação:

1. Identificar o repositório e sua finalidade.
2. Verificar a raiz do projeto.
3. Consultar o estado atual do Git.
4. Identificar a branch atual.
5. Verificar alterações locais e arquivos não rastreados.
6. Consultar as branches disponíveis.
7. Identificar convenções de commits e colaboração.
8. Consultar a documentação existente.

Comandos úteis:

```bash
git rev-parse --show-toplevel
git remote -v
git status
git branch
git branch -a
git log --oneline -10
```

### Procedimento obrigatório antes de commits ou pushes (Política Global de Git)

Antes de qualquer `commit` ou `push`:

1. Identifique o projeto em que está trabalhando.
2. Execute `git rev-parse --show-toplevel`.
3. Confirme que a raiz Git pertence ao projeto correto.
4. Execute `git status`.
5. Confira `git remote -v`.
6. Faça *staging* seletivo apenas dos arquivos pertencentes ao projeto (`git add <arquivo>`). **Não utilize `git add .` ou `git add -A` indiscriminadamente.**
7. Execute `git diff --cached --name-only`.
8. Revise todos os arquivos *staged*.
9. Confirme que nenhum arquivo externo (da `AI_workspace`: `AGENTS.md`, `00-GLOBAL/`, `01-PROJECTS/`, `02-KNOWLEDGE/`, `03-TEMPLATES/`, `.agents/`) ou de outro projeto será enviado.
10. Só então realize o commit.

Cada projeto deve manter seu próprio histórico Git e seu próprio endereço remoto. Se houver dúvida sobre a raiz, o remote ou a origem de um arquivo, interrompa a operação e informe o problema.

Não presumir que o repositório está atualizado ou que as alterações locais podem ser descartadas.

## 4. Gerenciamento de branches

Seguir a estratégia de branches já adotada pelo projeto.

Quando não existir uma convenção definida, sugerir uma organização simples e consistente.

Exemplos de nomenclatura:

- `main`: versão principal.
- `develop`: integração do desenvolvimento, quando utilizada.
- `feature/nome-da-funcionalidade`: novas funcionalidades.
- `fix/nome-do-problema`: correções.
- `docs/nome-da-documentacao`: documentação.
- `refactor/nome-da-alteracao`: refatorações.

Antes de criar, excluir ou modificar branches:

- Verificar o estado do repositório.
- Identificar possíveis alterações pendentes.
- Avaliar impactos sobre o trabalho da equipe.
- Solicitar autorização quando a operação alterar o estado remoto ou o histórico compartilhado.

## 5. Padrões de commits

Priorizar commits pequenos, objetivos e relacionados a uma única finalidade.

Seguir a convenção já utilizada pelo projeto.

Quando não existir uma convenção, recomendar mensagens descritivas.

Exemplos:

```text
feat: adiciona autenticação de usuários
fix: corrige validação do formulário
docs: atualiza documentação do projeto
refactor: reorganiza serviços da aplicação
test: adiciona testes de autenticação
style: ajusta responsividade do painel
chore: atualiza dependências
```

### Boas práticas

- Descrever o que foi alterado.
- Evitar mensagens vagas.
- Não agrupar alterações independentes.
- Não incluir arquivos desnecessários ou externos à pasta do projeto.
- Verificar o conteúdo do commit (`git diff --cached --name-only`) antes de criá-lo.

Commits locais pequenos e frequentes estão autorizados nos repositórios dos projetos após cumprir os 10 passos de verificação. Operações como `git push`, `git merge`, `git rebase`, alteração de remotos e reescrita de histórico exigem autorização explícita.

## 6. GitHub Issues

Ao criar ou organizar Issues, utilizar descrições claras e executáveis.

Uma Issue deve conter, quando aplicável:

- Título objetivo.
- Contexto.
- Problema ou necessidade.
- Objetivo.
- Descrição da implementação esperada.
- Critérios de aceite.
- Dependências.
- Responsável.
- Labels.
- Milestone.

### Critérios de qualidade

Uma Issue deve permitir que outro integrante compreenda o que precisa ser feito sem depender de explicações informais.

Evitar tarefas vagas, duplicadas ou excessivamente abrangentes.

## 7. GitHub Projects

Auxiliar na organização e acompanhamento das atividades da equipe.

Considerar:

- Backlog.
- A fazer.
- Em andamento.
- Em revisão.
- Concluído.

Os nomes das colunas devem respeitar o padrão já adotado pelo projeto.

### Organização das tarefas

Cada tarefa deve apresentar:

- Identificação.
- Título.
- Descrição.
- Responsável, quando definido.
- Prioridade, quando aplicável.
- Status.
- Critérios de conclusão.
- Dependências.
- Sprint ou milestone, quando utilizado.

### Planejamento

Ao organizar sprints:

1. Identificar os objetivos da sprint.
2. Verificar tarefas pendentes.
3. Identificar dependências.
4. Avaliar a capacidade da equipe.
5. Distribuir atividades conforme as responsabilidades definidas.
6. Estabelecer critérios de conclusão.
7. Acompanhar bloqueios e progresso.

Não inventar responsáveis, prazos ou estimativas como se fossem decisões da equipe.

## 8. Pull Requests

Ao preparar um Pull Request, incluir:

- Título objetivo.
- Contexto da alteração.
- Problema resolvido.
- Principais modificações.
- Evidências ou capturas de tela, quando pertinentes.
- Testes executados.
- Issues relacionadas.
- Pendências conhecidas.

Antes de recomendar a aprovação:

- Analisar o diff.
- Verificar possíveis regressões.
- Identificar problemas de segurança.
- Conferir compatibilidade com a arquitetura.
- Verificar testes e validações.
- Identificar alterações fora do escopo.

Não aprovar ou realizar merge automaticamente.

## 9. Revisão de código

Durante revisões:

- Priorizar problemas que afetem funcionamento.
- Identificar falhas de lógica.
- Verificar tratamento de erros.
- Avaliar segurança.
- Verificar qualidade e legibilidade.
- Identificar duplicações.
- Avaliar impactos em outras funcionalidades.
- Diferenciar problemas críticos de sugestões de melhoria.

Toda observação deve apresentar:

1. Arquivo e localização.
2. Problema identificado.
3. Impacto.
4. Sugestão de correção.

Não apontar preferências pessoais como se fossem defeitos técnicos.

## 10. Documentação do repositório

Manter documentação organizada e atualizada.

Considerar:

- README.
- Guia de instalação.
- Instruções de execução.
- Arquitetura.
- Estrutura de diretórios.
- Tecnologias e dependências.
- Fluxo de contribuição.
- Convenções de commits.
- Instruções de testes.

Não documentar funcionalidades que não foram confirmadas no código.

## 11. Segurança e operações críticas

Nunca expor tokens, senhas ou credenciais.

Antes de operações importantes:

- Verificar o repositório.
- Confirmar a branch.
- Identificar arquivos afetados.
- Avaliar o impacto.
- Confirmar a autorização.

Exigem autorização explícita:

- Commit.
- Push.
- Merge.
- Exclusão de branches.
- Exclusão de repositórios.
- Reescrita de histórico.
- Alteração de permissões.
- Publicação de releases.
- Alterações remotas em Issues e Projects.

Não executar comandos destrutivos sem autorização.

## 12. Integrações e ferramentas

Quando houver integração com GitHub por MCP, API ou outra ferramenta:

- Utilizar apenas ferramentas disponíveis e autorizadas.
- Verificar as permissões concedidas.
- Respeitar o escopo de acesso.
- Confirmar os resultados das operações.
- Não afirmar que uma ação foi realizada sem confirmação da ferramenta.

Quando não houver integração disponível, fornecer os comandos ou procedimentos manuais necessários.

## 13. Fluxo de trabalho recomendado

Para tarefas de gerenciamento:

1. Analisar o contexto.
2. Identificar o repositório e o objetivo.
3. Consultar o estado atual.
4. Planejar as operações.
5. Executar somente as ações autorizadas.
6. Conferir os resultados.
7. Atualizar a documentação quando necessário.
8. Apresentar um resumo da execução.

## 14. Resultado esperado

Ao finalizar, informar:

- Repositório envolvido.
- Operações realizadas.
- Arquivos ou registros modificados.
- Issues, Pull Requests ou Projects envolvidos.
- Validações realizadas.
- Problemas encontrados.
- Pendências.

## 15. Princípio fundamental

Manter o GitHub como fonte organizada e rastreável do trabalho da equipe.

Toda alteração deve ter uma finalidade clara, respeitar o fluxo de colaboração e preservar a integridade do histórico e dos repositórios.