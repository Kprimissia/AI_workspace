# AGENTS.md — ConsorTech

## 1. Identificação do projeto

**Nome:** ConsorTech  
**Tipo:** Sistema de comunicação e apoio operacional para consórcios.  
**Contexto:** Projeto desenvolvido no âmbito de uma atividade do SENAI, em parceria com a empresa F M C CENTER CAR LTDA.

### Objetivo

O ConsorTech tem como objetivo otimizar o processo de comunicação e baixa de clientes contemplados em consórcios.

A solução busca apoiar a comunicação com clientes contemplados, organizar informações e melhorar o acompanhamento das etapas relacionadas ao processo.

O sistema deve ser tratado como uma solução de comunicação, e não apenas como um sistema genérico de gerenciamento.

## 2. Organização do projeto e repositórios

O projeto possui frentes separadas de desenvolvimento e documentação (localizadas em `C:\Users\kaiqu\OneDrive\Desktop\SystemEx-PI`), cada uma com seu próprio repositório Git independente:

- **Front-end (`front-end`):** interface e interação com os usuários (`https://github.com/SystemX-PI/Front-End.git`).
- **Back-end (`Back-end`):** regras de negócio, processamento, persistência e disponibilização de dados por meio de APIs (`https://github.com/SystemX-PI/Back-end.git`).
- **Documentação e Arquitetura (`documentação-e-arquitetura`):** artefatos documentais e arquiteturais do projeto (`https://github.com/SystemEx-PI/Documentacao-e-Arquitetura.git`).

Respeitar rigorosamente a separação de responsabilidades e de histórico Git entre os repositórios.

Não presumir que uma funcionalidade está disponível no back-end apenas porque existe uma tela correspondente no front-end.

## 3. Tecnologias conhecidas

### Front-end

Tecnologias identificadas no desenvolvimento:

- React 19.
- TypeScript.
- Vite.
- React Router DOM 7.
- CSS.
- Oxlint.

A versão e as dependências efetivamente instaladas devem ser conferidas no `package.json` antes de qualquer alteração.

### Back-end

Consultar o repositório do back-end para identificar:

- Linguagem e framework.
- Estrutura de pastas.
- Banco de dados.
- Modelos e entidades.
- Rotas e endpoints.
- Autenticação e autorização.
- Integrações externas.

Não presumir tecnologias ou contratos de API sem verificar o código e a documentação.

## 4. Funcionalidades e módulos conhecidos

O desenvolvimento do front-end já contempla ou contempla parcialmente os seguintes módulos:

### Autenticação
- Login.
- Cadastro.
- Gerenciamento de sessão por token.
- Redirecionamento conforme o perfil de acesso.

### Área administrativa
- Painel administrativo.
- Área de integrações.
- Organização de funcionalidades destinadas aos funcionários e administradores.

### Portal do cliente
- Área destinada aos clientes.
- Redirecionamento de usuários com perfil de cliente para `/portal`.

### Integrações
- Configuração de integração com Gmail.
- Área demonstrativa de integração com WhatsApp.
- Organização de notificações e comunicações.

### Fila de notificações
- Recebimento de dados relacionados a clientes contemplados.
- Organização de notificações.
- Possibilidade de reenvio associado a um identificador de comunicação, conforme os contratos disponíveis.

**Atenção:** a existência de uma tela não significa que sua funcionalidade esteja totalmente integrada ou operacional.

## 5. Regras de desenvolvimento

- Respeitar a arquitetura existente.
- Analisar os repositórios antes de implementar funcionalidades.
- Manter a separação entre front-end e back-end.
- Utilizar TypeScript de maneira consistente no front-end.
- Reutilizar componentes e serviços quando apropriado.
- Evitar duplicação de código.
- Respeitar os contratos reais das APIs.
- Não criar endpoints fictícios.
- Não simular integrações como se fossem funcionais.
- Não alterar tecnologias ou arquitetura sem justificativa.

## 6. Integração entre front-end e back-end

Antes de implementar ou modificar uma integração:

1. Consultar o endpoint correspondente no back-end.
2. Verificar método HTTP, parâmetros e estrutura dos dados.
3. Conferir autenticação e autorização exigidas.
4. Verificar os possíveis códigos de resposta e erros.
5. Implementar o consumo da API respeitando seu contrato.
6. Validar o comportamento integrado, quando possível.

A URL da API no front-end utiliza a variável de ambiente `VITE_API_URL`.

No ambiente de desenvolvimento, existe uma configuração de proxy do Vite para `/api`, direcionada ao servidor local na porta `8080`. Confirmar a configuração atual antes de modificá-la.

## 7. Segurança

- Proteger informações de clientes.
- Não expor tokens ou credenciais.
- Respeitar os níveis de acesso dos usuários.
- Não confiar exclusivamente nas restrições implementadas no front-end.
- Validar permissões e regras de negócio no back-end.
- Não armazenar informações sensíveis sem necessidade.
- Avaliar os riscos de qualquer alteração relacionada à autenticação.

## 8. Organização e colaboração da equipe

O projeto é desenvolvido em equipe.

Portanto:

- Preservar alterações realizadas por outros integrantes.
- Verificar o estado do Git antes de modificar arquivos.
- Não sobrescrever implementações existentes.
- Respeitar as responsabilidades e divisões de trabalho.
- Manter comunicação clara sobre alterações que afetem outros módulos.
- Evitar mudanças fora do escopo da tarefa.

## 9. Política de Git, Isolamento e Autonomia de Commits

Este projeto herda integralmente a **Política Global de Git** definida em `00-GLOBAL/RULES/global-rules.md` (Seção 8):

### 9.1. Autonomia e limites
- **Commits locais autorizados:** O agente tem autonomia para realizar commits locais pequenos, frequentes e descritivos (em português) no repositório específico que estiver sendo trabalhado (`front-end`, `Back-end` ou `documentação-e-arquitetura`), sem pedir autorização individual para cada commit.
- **Operações que exigem autorização explícita:** `git push`, `git merge`, `git rebase`, alteração de remotos e qualquer operação que reescreva o histórico compartilhado.

### 9.2. Isolamento entre os repositórios do ConsorTech e proteção contra arquivos externos
Antes de qualquer commit ou push, execute obrigatoriamente os 10 passos globais:
1. Identifique em qual sub-repositório do ConsorTech está trabalhando (`front-end`, `Back-end` ou `documentação-e-arquitetura`).
2. Execute `git rev-parse --show-toplevel` e confirme que a raiz Git corresponde exatamente àquele sub-repositório (e não à pasta pai nem à `AI_workspace`).
3. Execute `git status` e confira `git remote -v` (`SystemX-PI/Front-End.git`, `SystemX-PI/Back-end.git` ou `SystemEx-PI/Documentacao-e-Arquitetura.git`).
4. Faça *staging* seletivo (`git add <arquivo>`), **nunca** utilizando `git add .` ou `git add -A` indiscriminadamente.
5. **Atenção especial no `Back-end`:** Nunca inclua arquivos compilados da pasta `bin/` (`*.class`) nos commits; faça staging apenas de código-fonte (`src/`), configurações (`pom.xml`, etc.), testes e documentações legítimas do repositório.
6. **Bloqueio de arquivos externos:** Confirme via `git diff --cached --name-only` que nenhum arquivo interno da `AI_workspace` (`AGENTS.md` da workspace, `00-GLOBAL/`, `01-PROJECTS/`, `02-KNOWLEDGE/`, `03-TEMPLATES/`) ou de outro projeto foi incluído, preservando os arquivos legítimos do próprio ConsorTech.

## 10. Documentação

Manter documentação relacionada a:

- Requisitos funcionais e não funcionais.
- Arquitetura do sistema.
- Regras de negócio.
- Contratos de API.
- Estrutura dos módulos.
- Integrações.
- Segurança.
- Testes e validações.
- Decisões técnicas.

A documentação deve refletir o funcionamento real do sistema.

## 11. Diretrizes para o agente

Antes de iniciar qualquer tarefa:

1. Identificar se a solicitação pertence ao front-end, back-end ou à gestão do projeto.
2. Consultar este arquivo e as instruções adicionais.
3. Inspecionar os arquivos e repositórios envolvidos.
4. Identificar dependências e impactos.
5. Apresentar um plano quando a tarefa for complexa.

Ao concluir:

- Informar arquivos modificados.
- Explicar as principais decisões.
- Apresentar validações realizadas.
- Identificar pendências e limitações.
- Não declarar funcionalidades como concluídas sem comprovação.

## 12. Informações ainda a confirmar

O agente deve investigar os repositórios e a documentação antes de assumir informações sobre:

- Tecnologias e versões do back-end.
- Banco de dados utilizado.
- Arquitetura definitiva.
- Endpoints efetivamente implementados.
- Contratos de integração com Gmail e WhatsApp.
- Regras completas de negócio.
- Perfis e permissões definitivos.
- Responsabilidades individuais dos integrantes.
- Estado atual de cada funcionalidade.

Não preencher essas lacunas com suposições.