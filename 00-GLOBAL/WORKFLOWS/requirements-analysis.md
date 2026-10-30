# Workflow — Análise de Requisitos e Planejamento de Funcionalidades

## Objetivo

Orientar o agente na compreensão, análise, organização e transformação de solicitações em requisitos claros, verificáveis e implementáveis.

## 1. Compreender a solicitação

Antes de propor uma solução:

- Identificar o problema que precisa ser resolvido.
- Entender o objetivo da funcionalidade.
- Identificar quem utilizará o recurso.
- Compreender o contexto do projeto.
- Identificar restrições técnicas e funcionais.
- Verificar se existem informações incompletas ou contraditórias.

Não começar a implementação antes de compreender suficientemente o que foi solicitado.

## 2. Consultar o projeto

Investigar:

- Documentação existente.
- Estrutura do repositório.
- Funcionalidades relacionadas.
- Componentes e módulos existentes.
- Contratos de API.
- Regras de negócio implementadas.
- Tecnologias e dependências.
- Restrições definidas pela equipe.

Não propor funcionalidades que contradigam decisões já estabelecidas sem apresentar o conflito.

## 3. Identificar os tipos de requisitos

Separar as necessidades em:

### Requisitos funcionais

Descrevem o que o sistema deve fazer.

Exemplos:
- Permitir autenticação de usuários.
- Exibir notificações.
- Cadastrar informações.
- Consultar registros.
- Enviar comunicações.

### Requisitos não funcionais

Descrevem características e restrições de qualidade.

Exemplos:
- Segurança.
- Desempenho.
- Acessibilidade.
- Responsividade.
- Disponibilidade.
- Manutenibilidade.
- Compatibilidade.

### Regras de negócio

Descrevem condições e comportamentos específicos do domínio do sistema.

Não confundir regras de negócio com decisões de implementação.

## 4. Identificar dúvidas e dependências

Verificar:

- Informações ausentes.
- Regras não definidas.
- Dependências entre funcionalidades.
- Integrações externas.
- Necessidade de alterações no back-end.
- Necessidade de alterações no banco de dados.
- Restrições de segurança.
- Dependências de outros integrantes.

Quando uma informação essencial estiver ausente, fazer uma pergunta objetiva antes de assumir uma solução.

## 5. Definir critérios de aceitação

Cada requisito implementável deve possuir critérios que permitam verificar sua conclusão.

Os critérios devem ser:

- Claros.
- Objetivos.
- Testáveis.
- Relacionados ao comportamento esperado.
- Livres de interpretações desnecessárias.

Exemplo:

**Requisito:** permitir que um usuário realize login.

**Critérios de aceitação:**
- O usuário consegue informar suas credenciais.
- O sistema valida as informações.
- Credenciais inválidas geram uma mensagem adequada.
- O acesso é concedido somente após autenticação válida.
- O comportamento respeita as permissões do usuário.

## 6. Decompor em tarefas

Transformar requisitos em atividades menores.

Cada tarefa deve conter:

- Título objetivo.
- Descrição.
- Objetivo.
- Arquivos ou módulos potencialmente envolvidos.
- Dependências.
- Critérios de aceitação.
- Forma de validação.

Separar atividades de front-end, back-end, banco de dados, testes e documentação quando isso facilitar a organização da equipe.

## 7. Priorizar requisitos

Considerar:

- Valor para o usuário.
- Importância para o funcionamento do sistema.
- Urgência.
- Riscos.
- Dependências.
- Esforço estimado.

Quando necessário, utilizar técnicas de priorização como MoSCoW:

- Must have: indispensável.
- Should have: importante.
- Could have: desejável.
- Won't have: fora do escopo atual.

Não confundir prioridade com ordem de implementação.

## 8. Planejar a execução

Organizar as tarefas considerando:

- Dependências técnicas.
- Sequência lógica.
- Capacidade da equipe.
- Prazo disponível.
- Riscos.
- Necessidade de validações intermediárias.

Para atividades extensas, dividir a execução em etapas menores.

## 9. Registrar e documentar

Quando aplicável, registrar os resultados em:

- Backlog.
- GitHub Issues.
- GitHub Projects.
- Histórias de usuário.
- Especificações funcionais.
- Critérios de aceitação.
- Documentação do projeto.

Respeitar os padrões e ferramentas já utilizados pela equipe.

## 10. Validar o planejamento

Antes de considerar a análise concluída, verificar:

- Todos os requisitos foram compreendidos?
- Existem ambiguidades?
- Os critérios de aceitação são verificáveis?
- As dependências foram identificadas?
- As tarefas possuem escopo definido?
- Existem riscos relevantes?
- O planejamento respeita as restrições do projeto?

## 11. Relatório final

Apresentar:

- Problema identificado.
- Objetivo da funcionalidade.
- Requisitos funcionais.
- Requisitos não funcionais.
- Regras de negócio.
- Dúvidas e dependências.
- Critérios de aceitação.
- Tarefas propostas.
- Prioridades.
- Riscos e próximos passos.

## Regras obrigatórias

1. Não inventar requisitos ou regras de negócio.
2. Não assumir informações essenciais sem validação.
3. Não confundir funcionalidades desejadas com funcionalidades existentes.
4. Não propor alterações fora do escopo sem justificativa.
5. Considerar a arquitetura e as tecnologias reais do projeto.
6. Priorizar requisitos claros e verificáveis.
7. Registrar dependências entre equipes.
8. Não iniciar implementações complexas sem planejamento adequado.