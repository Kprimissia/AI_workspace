# Guia Técnico: Git, GitHub e Fluxos de Colaboração em Equipe

## 1. Visão Geral e Conceitos Fundamentais

O **Git** e o **GitHub** garantem rastreabilidade, revisão por pares e segurança no desenvolvimento compartilhado. Em ambientes colaborativos assistidos por agentes de IA, **a preservação do trabalho da equipe e o respeito às autorizações são regras absolutas**.

### Conceitos Essenciais
- **Working Tree, Staging Area (`Index`) e HEAD:** Compreender o que está modificado localmente (`git status` / `git diff`), o que está preparado para commit (`git diff --staged`) e qual é o commit atual (`HEAD`).
- **Branches Isoladas por Tarefa:** Cada funcionalidade, correção ou refatoração deve ser desenvolvida em uma branch própria (`feature/...`, `fix/...`, `docs/...`, `refactor/...`), mantendo a branch principal (`main` / `develop`) estável.
- **Conventional Commits:** Padronização semântica de mensagens de commit (`feat:`, `fix:`, `docs:`, `refactor:`, `test:`, `style:`, `chore:`).

---

## 2. Boas Práticas e Regras de Segurança Operacional

1. **Procedimento Obrigatório Antes de Commits ou Pushes (10 Passos):**
   Antes de qualquer `commit` ou `push`:
   1. Identifique o projeto em que está trabalhando.
   2. Execute `git rev-parse --show-toplevel`.
   3. Confirme que a raiz Git pertence ao projeto correto.
   4. Execute `git status`.
   5. Confira `git remote -v`.
   6. Faça *staging* seletivo apenas dos arquivos pertencentes ao projeto (`git add <arquivo>`). **Não utilize `git add .` ou `git add -A` indiscriminadamente.**
   7. Execute `git diff --cached --name-only`.
   8. Revise todos os arquivos *staged*.
   9. Confirme que nenhum arquivo externo (da `AI_workspace`: `AGENTS.md`, `00-GLOBAL/`, `01-PROJECTS/`, `02-KNOWLEDGE/`, `03-TEMPLATES/`, `.agents/`) ou de outro projeto será enviado, preservando todos os arquivos legítimos do próprio projeto.
   10. Só então realize o commit.
   - Se houver qualquer dúvida sobre a raiz, o remote ou a origem de um arquivo, interrompa a operação e informe o problema.
2. **Autonomia de Desenvolvimento e Operações que Exigem Autorização Explícita:**
   - **Permitido com autonomia:** Desenvolver, corrigir, testar, documentar e realizar **commits locais pequenos e frequentes** no repositório do projeto (cumprindo os 10 passos acima).
   - **Exige autorização explícita do usuário (nunca executar por conta própria):**
     - `git push` (envio ao repositório remoto)
     - `git merge` ou `git rebase`
     - Alteração de remotos (`git remote set-url`, `add`, `remove`)
     - Exclusão de branches (`git branch -D` / `git push origin --delete`)
     - Comandos destrutivos ou reescrita de histórico (`git reset --hard`, `git checkout -- .`, `git restore .`, `git clean -fd`).
3. **Commits Atômicos e Seguros:**
   - Quando autorizado a criar um commit, adicione apenas os arquivos pertinentes à tarefa (`git add <arquivo>`), revise `git diff --staged` para garantir que nenhum `.env`, credencial ou arquivo temporário foi incluído, e escreva mensagens claras em português.
4. **Pull Requests e Code Review:**
   - Todo Pull Request deve descrever o problema resolvido, as alterações técnicas realizadas, como testar/validar e vincular a Issue correspondente (`Closes #123`).

---

## 3. Exemplos Práticos

### 3.1. Diagnóstico Seguro de Repositório e Comparação entre Branches

```bash
# 1. Verificar estado atual sem alterar nada
git status --short --branch

# 2. Inspecionar diferenças locais ainda não preparadas
git diff

# 3. Comparar a branch atual com a branch principal (ex.: main)
git diff main...HEAD --stat

# 4. Consultar quem alterou um trecho específico e por quê
git log -S "VITE_API_URL" --oneline
```

### 3.2. Padrão de Mensagens de Commit (Português)

```text
feat(notificacoes): adiciona filtro por status na fila de contemplados
fix(auth): corrige redirecionamento de clientes para a rota /portal
docs(api): documenta contrato do endpoint de reenvio de comunicacao
refactor(servicos): centraliza tratamento de erros HTTP no cliente de API
test(login): adiciona testes de validacao para credenciais invalidas
```

---

## 4. Erros Comuns e Como Evitá-los

| Erro Comum | Problema | Solução Recomendada |
| :--- | :--- | :--- |
| **Executar `git add .` sem revisar `git status`** | Inclui acidentalmente arquivos `.env`, logs, builds (`dist/`, `node_modules/`) ou alterações de outra tarefa. | Verificar `git status`, configurar corretamente o `.gitignore` e adicionar arquivos explicitamente. |
| **Usar `git push --force` em branches compartilhadas** | Sobrescreve e apaga commits de outros integrantes da equipe. | Nunca reescrever histórico compartilhado; se necessário em branch própria e com autorização, usar `--force-with-lease`. |
| **Resolver conflitos descartando alterações alheias** | Apaga funcionalidades implementadas por colegas de equipe. | Analisar ambos os lados do conflito (`HEAD` vs branch recebida) e preservar a lógica combinada. |

---

## 5. Referências Oficiais

- **Pro Git Book (Documentação Oficial Git):** https://git-scm.com/book/pt-br/v2
- **GitHub Docs:** https://docs.github.com/pt
- **Conventional Commits Specification:** https://www.conventionalcommits.org/pt-br/v1.0.0/

