# AGENTS.md — FRONTEND-LESSONS

## 1. Objetivo do projeto

Este projeto reúne as atividades da disciplina de Front-End, da atividade 01 até a atividade 08.

O objetivo é desenvolver todas as atividades propostas pelo professor, respeitando fielmente os materiais originais, a sequência de aprendizagem e os requisitos de cada exercício.

O trabalho deve resultar em um repositório organizado, com todas as atividades implementadas e um histórico Git detalhado, cronológico e composto por commits pequenos e significativos.

## 2. Fonte oficial das atividades

A principal referência é o repositório GitHub do professor.

Antes de iniciar:
- Identifique o repositório oficial do professor.
- Analise as aulas e os materiais disponíveis.
- Localize as atividades 01, 02, 03, 04, 05, 06, 07 e 08.
- Leia os enunciados, instruções, exemplos e critérios de entrega.
- Identifique dependências entre as atividades.
- Utilize os materiais originais como fonte principal.

Se o endereço do repositório do professor ainda não estiver configurado, solicite o link ao usuário antes de começar.

Não invente requisitos, não pule etapas e não substitua atividades por implementações diferentes.

## 3. Regras de desenvolvimento

Execute as atividades rigorosamente em ordem:

1. Atividade 01.
2. Atividade 02.
3. Atividade 03.
4. Atividade 04.
5. Atividade 05.
6. Atividade 06.
7. Atividade 07.
8. Atividade 08.

Para cada atividade:

1. Leia integralmente o material correspondente.
2. Identifique todos os requisitos.
3. Analise o código existente e a estrutura do projeto.
4. Planeje a implementação.
5. Desenvolva a solução completa.
6. Execute os testes e validações aplicáveis.
7. Corrija erros encontrados.
8. Confira se todos os requisitos foram atendidos.
9. Registre as alterações no Git.
10. Atualize a documentação, quando necessário.

Não comece a próxima atividade enquanto a atual estiver incompleta.

## 4. Qualidade do código

- Siga os padrões e tecnologias utilizados nas aulas.
- Priorize o aprendizado demonstrado pelo professor.
- Utilize código organizado, legível e de fácil manutenção.
- Evite complexidade desnecessária.
- Não adicione bibliotecas sem necessidade.
- Não implemente funcionalidades que não foram solicitadas.
- Não remova funcionalidades existentes sem justificativa.
- Preserve a identidade e a organização do projeto.
- Não copie soluções sem compreender sua finalidade.
- Não declare testes aprovados sem executá-los.

A implementação deve demonstrar domínio progressivo dos conteúdos ensinados.

## 5. Estratégia obrigatória de Git

O histórico de commits é parte importante da entrega.

O usuário autoriza expressamente que o agente realize commits locais automaticamente durante o desenvolvimento deste projeto, sem solicitar autorização individual para cada commit.

### 5.1 Frequência dos commits

Faça commits pequenos, frequentes e organizados.

Não concentre uma atividade inteira em um único commit.

Sempre que houver uma alteração lógica e funcionalmente coerente, considere registrá-la em um commit próprio.

Exemplos de separação:

- Configuração inicial.
- Estrutura de diretórios.
- Criação de componentes.
- Implementação de funcionalidades.
- Criação de páginas.
- Estilização.
- Responsividade.
- Validações.
- Correções de bugs.
- Refatorações.
- Documentação.
- Testes.

Faça quantos commits forem necessários para representar o desenvolvimento real, sem criar alterações artificiais.

### 5.2 Padrão das mensagens

Utilize mensagens em português, com prefixos convencionais:

- `feat:` novas funcionalidades.
- `fix:` correções.
- `style:` alterações visuais e formatação.
- `refactor:` melhorias internas.
- `docs:` documentação.
- `test:` testes.
- `chore:` configurações e manutenção.

Exemplos:

- `chore: configura estrutura inicial da atividade 01`
- `feat: implementa estrutura principal da página`
- `feat: adiciona componente de navegação`
- `style: ajusta layout e espaçamentos`
- `fix: corrige comportamento do formulário`
- `test: valida funcionalidades da atividade 01`
- `docs: documenta implementação da atividade 01`

### 5.3 Ordem cronológica

- Os commits devem acompanhar a sequência real do desenvolvimento.
- Identifique a atividade correspondente nas mensagens quando apropriado.
- Finalize os commits de uma atividade antes de iniciar os da próxima.
- Não reescreva o histórico existente sem autorização.
- Não faça commits vazios.
- Não faça commits gigantes que misturem várias atividades.

### 5.4 Segurança do repositório, isolamento e procedimento obrigatório de commit

Este projeto herda a **Política Global de Git** (`00-GLOBAL/RULES/global-rules.md`, Seção 8). Como existem múltiplas pastas de atividades no ambiente local (ex.: `C:\Users\kaiqu\OneDrive\Desktop\Kaique\frontend-2s2026` apontando para `https://github.com/Kprimissia/frontend-2s2026.git` e subpastas com repositórios aninhados), é obrigatório seguir rigorosamente os 10 passos antes de qualquer commit ou push:

1. Identifique o projeto (`FRONTEND-2S2026` / `FRONTEND-LESSONS`) e a atividade atual (`01` a `08`).
2. Execute `git rev-parse --show-toplevel`.
3. Confirme que a raiz Git pertence ao repositório correto do projeto (evitando operar acidentalmente em subpastas com `.git` aninhado ou clones paralelos sem confirmação).
4. Execute `git status` (atenção a deleções `D` ou arquivos não rastreados `??` pendentes na árvore de trabalho).
5. Confira `git remote -v` (confirmando o repositório oficial da disciplina do aluno, ex.: `Kprimissia/frontend-2s2026.git`, e nunca um remote genérico como `SEU-USUARIO/atividade01.git`).
6. Faça *staging* seletivo apenas dos arquivos pertencentes à etapa/atividade atual (`git add <arquivo>`). **Não utilize `git add .` ou `git add -A` indiscriminadamente.**
7. Execute `git diff --cached --name-only`.
8. Revise todos os arquivos *staged*.
9. Confirme que nenhum arquivo interno da `AI_workspace` (`AI_workspace/AGENTS.md`, `00-GLOBAL/`, `01-PROJECTS/`, `02-KNOWLEDGE/`, `03-TEMPLATES/`, Skills, Workflows ou Prompts globais) nem arquivos de outros projetos serão enviados, preservando integralmente os arquivos legítimos das atividades (código-fonte, `package.json`, configurações e `README.md` de entrega).
10. Só então realize o commit.

Se houver dúvida sobre qual pasta local é a raiz canônica da atividade ou sobre a origem de um arquivo, interrompa a operação e informe o problema ao usuário.

Nunca:
- Faça commits na raiz da `AI_workspace`.
- Misture arquivos de outros projetos.
- Utilize `git add .` ou `git add -A` sem seleção explícita.
- Altere o endereço remoto sem autorização.
- Apague ou reescreva histórico existente sem autorização.
- Inclua arquivos pessoais, credenciais ou segredos.
- Faça `push`, `merge` ou deploy sem autorização explícita.

**Autorização permanente:** commits locais pequenos e frequentes relacionados ao desenvolvimento deste projeto estão autorizados. `git push` para o GitHub continua dependendo de autorização explícita do usuário.

## 6. Organização das atividades

Mantenha as atividades organizadas e identificáveis.

Sempre que compatível com a estrutura exigida pelo professor, utilize uma organização semelhante a:

- `atividade-01/`
- `atividade-02/`
- `atividade-03/`
- `atividade-04/`
- `atividade-05/`
- `atividade-06/`
- `atividade-07/`
- `atividade-08/`

Não force essa estrutura se o professor exigir outra organização.

Cada atividade deve preservar seus arquivos, códigos e requisitos de entrega.

## 7. Revisão e validação

Antes de considerar uma atividade concluída:

- Confira todos os itens do enunciado.
- Verifique se os arquivos necessários existem.
- Execute a aplicação quando aplicável.
- Execute os testes disponíveis.
- Verifique erros de compilação, execução e lint.
- Analise a organização do código.
- Confira se os commits correspondem às alterações reais.

Se algum requisito não puder ser atendido, documente o motivo e informe o usuário.

## 8. Continuidade automática

Quando o usuário solicitar a realização das próximas atividades, continue de onde o trabalho parou.

Antes de começar:
- Consulte este arquivo.
- Consulte o histórico Git.
- Verifique quais atividades já foram concluídas.
- Identifique a próxima atividade pendente.
- Consulte novamente o material original do professor.
- Preserve o trabalho já realizado.

Não reinicie o projeto sem necessidade.

Não peça autorização para tarefas de desenvolvimento e commits locais já autorizadas por estas instruções.

Se o usuário solicitar todas as atividades, execute sequencialmente da 01 à 08.

Se solicitar apenas a próxima atividade, execute somente a próxima pendente.

## 9. Relatórios

Ao concluir cada atividade, informe:

- Atividade concluída.
- Requisitos atendidos.
- Arquivos criados ou modificados.
- Testes executados e resultados.
- Quantidade e identificação dos commits realizados.
- Pendências encontradas.

Ao finalizar as oito atividades, apresente um relatório consolidado com o estado final do projeto e do histórico Git.

## 10. Prioridades

Em caso de conflito entre instruções, siga esta ordem:

1. Enunciados e requisitos oficiais do professor.
2. Segurança e integridade do repositório.
3. Regras deste AGENTS.md.
4. Regras globais da AI_workspace.
5. Boas práticas gerais de desenvolvimento.

O resultado deve ser fiel às aulas, tecnicamente correto, organizado e acompanhado de um histórico Git que represente o trabalho efetivamente realizado.