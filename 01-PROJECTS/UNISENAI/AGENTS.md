# AGENTS.md — UniSENAI

## 1. Identificação do projeto

**Projeto:** UniSENAI  
**Área de atuação do agente:** Desenvolvimento Front-end  
**Escopo:** Interface, experiência do usuário, componentes e integração do front-end com serviços existentes.

Este arquivo estabelece as instruções específicas para agentes de inteligência artificial que trabalham neste projeto.

## 2. Restrição principal de atuação

O agente deve trabalhar exclusivamente no front-end.

### Atividades permitidas

- Desenvolver interfaces e páginas.
- Criar e modificar componentes.
- Implementar funcionalidades visuais e interativas.
- Desenvolver formulários e validações no cliente.
- Implementar navegação e roteamento.
- Trabalhar com responsividade.
- Melhorar acessibilidade e experiência do usuário.
- Consumir APIs existentes.
- Corrigir erros relacionados ao front-end.
- Criar testes para componentes e funcionalidades de interface.
- Organizar e documentar o código front-end.

### Atividades não permitidas

- Desenvolver funcionalidades de back-end.
- Criar ou modificar endpoints.
- Alterar regras de negócio implementadas no servidor.
- Modificar estruturas de banco de dados.
- Criar migrations.
- Alterar autenticação no servidor.
- Modificar configurações ou arquivos exclusivos do back-end.
- Implementar serviços de servidor.
- Modificar infraestrutura ou implantação do back-end.

Se uma tarefa exigir alterações no back-end, o agente deve explicar a dependência, indicar o que precisa ser solicitado à equipe responsável e continuar apenas com as partes possíveis no front-end.

## 3. Análise inicial

Antes de começar qualquer tarefa:

1. Identificar a raiz do projeto.
2. Analisar a estrutura de diretórios.
3. Identificar as tecnologias e suas versões.
4. Consultar o `package.json` e os arquivos de configuração.
5. Identificar os padrões de componentes e estilos.
6. Verificar a arquitetura de navegação.
7. Consultar a documentação existente.
8. Verificar o estado do Git.

Não presumir tecnologias, bibliotecas ou padrões que não tenham sido identificados no projeto.

## 4. Padrões de desenvolvimento front-end

- Respeitar a arquitetura existente.
- Priorizar componentes reutilizáveis.
- Manter separação adequada de responsabilidades.
- Utilizar nomenclaturas consistentes.
- Evitar duplicação de código.
- Evitar dependências desnecessárias.
- Manter o código organizado e de fácil manutenção.
- Preservar funcionalidades existentes durante refatorações.
- Seguir os padrões de tipagem e formatação adotados pelo projeto.

Não introduzir novas tecnologias ou alterar a arquitetura sem justificativa técnica.

## 5. Interface e experiência do usuário

Toda implementação visual deve considerar:

- Consistência visual entre páginas.
- Hierarquia clara de informações.
- Navegação intuitiva.
- Responsividade para dispositivos móveis e desktops.
- Acessibilidade.
- Feedback visual para ações do usuário.
- Estados de carregamento.
- Estados vazios.
- Mensagens de erro.
- Confirmações de operações quando necessárias.

Evitar interfaces excessivamente complexas, elementos desnecessários e inconsistências de design.

## 6. Integração com APIs

O agente pode consumir APIs existentes, desde que respeite os contratos disponibilizados.

Antes de implementar uma integração:

1. Consultar a documentação disponível.
2. Identificar os endpoints existentes.
3. Verificar métodos HTTP e parâmetros.
4. Conferir os formatos de requisição e resposta.
5. Implementar o tratamento de erros.
6. Considerar carregamento e estados de falha.
7. Validar a integração quando possível.

Não criar endpoints fictícios ou modificar o servidor para fazer uma integração funcionar.

Quando o contrato da API estiver ausente ou incompleto, registrar a dependência e solicitar as informações necessárias.

## 7. Segurança no front-end

- Não armazenar credenciais ou segredos no código.
- Não expor chaves privadas.
- Não confiar na interface como mecanismo de autorização.
- Tratar dados recebidos de APIs adequadamente.
- Evitar exposição desnecessária de informações.
- Respeitar os mecanismos de autenticação existentes.
- Não contornar restrições de segurança do sistema.

## 8. Testes e qualidade

Quando aplicável:

- Executar verificações de lint.
- Executar testes automatizados.
- Validar o build.
- Verificar navegação e roteamento.
- Testar formulários e interações.
- Verificar responsividade.
- Identificar erros no console.
- Conferir possíveis regressões.

Não afirmar que uma funcionalidade está validada sem executar as verificações pertinentes.

## 9. Colaboração e Política de Git

O projeto é desenvolvido em equipe no repositório `C:\Users\kaiqu\OneDrive\Desktop\frontend` (remote oficial: `https://github.com/UniSENAI-Sorocaba/plataforma-frontend`) e herda integralmente a **Política Global de Git** (`00-GLOBAL/RULES/global-rules.md`, Seção 8).

### 9.1. Autonomia de commits locais e preservação da equipe
- **Preservação obrigatória:** Verificar `git status` antes de modificar arquivos e preservar alterações em andamento de outros integrantes ou tarefas (como branches de feature ativas).
- **Commits locais autorizados:** O agente pode realizar commits locais pequenos, frequentes e semânticos (em português) referentes às tarefas de Front-end executadas, sem solicitar autorização individual para cada commit.
- **Operações que exigem autorização explícita:** `git push`, `git merge`, `git rebase`, exclusão de branches, alteração de remotos, reescrita de histórico ou operações destrutivas.

### 9.2. Procedimento obrigatório antes de commits (10 passos) e isolamento
Antes de qualquer commit ou push:
1. Identifique o projeto UniSENAI e confirme a branch atual.
2. Execute `git rev-parse --show-toplevel` e confirme que a raiz é o repositório do front-end do UniSENAI.
3. Execute `git status` e confira `git remote -v` (`UniSENAI-Sorocaba/plataforma-frontend`).
4. Faça *staging* seletivo (`git add <arquivo>`) apenas dos arquivos pertencentes à tarefa de front-end. **Não utilize `git add .` ou `git add -A` indiscriminadamente** (para não incluir alterações não relacionadas que estejam no *working tree*).
5. Execute `git diff --cached --name-only` e revise todos os arquivos *staged*.
6. Confirme que nenhum arquivo interno da `AI_workspace` (`AI_workspace/AGENTS.md`, `00-GLOBAL/`, `01-PROJECTS/`, `02-KNOWLEDGE/`, `03-TEMPLATES/`) ou de outros projetos será enviado, mantendo apenas os arquivos legítimos do próprio repositório UniSENAI (código-fonte, testes, README, runbooks e configurações do projeto).
7. Se a raiz Git, o remote ou a origem de algum arquivo gerarem dúvida, interrompa a operação imediatamente e informe o usuário.

## 10. Documentação

Manter documentação relacionada ao front-end, incluindo:

- Estrutura de diretórios.
- Componentes.
- Páginas e rotas.
- Dependências.
- Configurações.
- Integrações com APIs.
- Procedimentos de execução.
- Testes e validações.

Documentar apenas informações verificadas.

## 11. Procedimento de execução

Para cada tarefa:

1. Entender o requisito.
2. Identificar os arquivos envolvidos.
3. Verificar se a tarefa pertence ao escopo front-end.
4. Analisar possíveis impactos.
5. Apresentar um plano quando a tarefa for complexa.
6. Implementar a solução.
7. Executar as validações disponíveis.
8. Informar alterações, resultados e pendências.

## 12. Tratamento de solicitações fora do escopo

Se o usuário solicitar uma alteração no back-end:

- Não realizar a implementação.
- Explicar por que a solicitação ultrapassa o escopo deste projeto.
- Identificar a dependência técnica.
- Descrever o que a equipe responsável pelo back-end precisa fornecer ou modificar.
- Quando possível, preparar a parte front-end que não dependa dessa alteração.

## 13. Princípio fundamental

O objetivo é desenvolver um front-end consistente, funcional, responsivo, acessível e sustentável, respeitando a arquitetura existente, a organização da equipe e os limites de atuação estabelecidos para este projeto.