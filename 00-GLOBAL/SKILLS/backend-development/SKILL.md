---
name: backend-development
description: Analisa, desenvolve, corrige, refatora e valida aplicações back-end. Utilize esta skill para trabalhar com APIs, servidores, regras de negócio, autenticação, autorização, bancos de dados, integrações, segurança e processamento de dados.
---

# Backend Development

## 1. Objetivo

Estabelecer um procedimento técnico reutilizável para desenvolver e manter aplicações back-end, priorizando segurança, confiabilidade, organização e integridade dos dados.

Esta Skill orienta o agente desde a análise da arquitetura até a implementação, integração e validação de funcionalidades do servidor.

## 2. Escopo

Esta Skill pode ser utilizada em atividades envolvendo:

- APIs REST.
- Servidores e aplicações back-end.
- Regras de negócio.
- Autenticação e autorização.
- Bancos de dados relacionais e não relacionais.
- Modelagem de dados.
- Operações CRUD.
- Integrações externas.
- Processamento de dados.
- Validação de entradas.
- Tratamento de erros.
- Logs e monitoramento.
- Testes automatizados.
- Segurança de aplicações.

As tecnologias devem ser identificadas no projeto. Não presumir linguagens, frameworks ou bancos de dados.

## 3. Análise inicial e sincronização obrigatória

Antes de implementar, testar ou subir qualquer funcionalidade:

1. Identificar o repositório e seu diretório raiz (`git rev-parse --show-toplevel`).
2. **Sincronizar obrigatoriamente o repositório com o remoto (`git fetch --all --prune` e `git pull --ff-only` em `main` e `develop`)** antes de analisar ou executar o projeto.
3. Consultar o `AGENTS.md` e demais instruções do projeto.
3. Identificar a linguagem e o framework utilizados.
4. Analisar a estrutura de diretórios.
5. Consultar arquivos de dependências e configurações.
6. Identificar a arquitetura da aplicação.
7. Examinar rotas, controladores, serviços e modelos existentes.
8. Identificar o banco de dados e a forma de acesso.
9. Verificar o estado do Git.
10. Compreender os requisitos e as regras de negócio.

Não modificar a arquitetura antes de compreender seu funcionamento atual.

## 4. Arquitetura e organização

Priorizar:

- Separação de responsabilidades.
- Baixo acoplamento.
- Alta coesão.
- Reutilização adequada.
- Organização por módulos ou domínios, conforme a arquitetura existente.
- Centralização apropriada de configurações.
- Tratamento consistente de erros.
- Facilidade de testes e manutenção.

Evitar:

- Lógica de negócio espalhada.
- Controladores excessivamente grandes.
- Duplicação de código.
- Dependências circulares.
- Abstrações desnecessárias.
- Acesso ao banco de dados sem organização adequada.

Respeitar a arquitetura existente e justificar mudanças estruturais.

## 5. Desenvolvimento de APIs

Ao desenvolver ou modificar uma API:

1. Identificar o recurso e sua finalidade.
2. Definir ou consultar o contrato da API.
3. Verificar o método HTTP apropriado.
4. Definir parâmetros, cabeçalhos e corpo da requisição.
5. Definir a estrutura das respostas.
6. Implementar validações.
7. Implementar regras de negócio.
8. Tratar erros.
9. Verificar autenticação e autorização.
10. Criar ou atualizar testes e documentação.

### Boas práticas

- Utilizar métodos HTTP adequados.
- Respeitar os princípios REST quando aplicáveis.
- Padronizar respostas.
- Utilizar códigos HTTP coerentes.
- Validar dados recebidos.
- Evitar exposição de informações internas.
- Não confiar nos dados enviados pelo cliente.
- Considerar paginação, filtros e limites quando necessários.
- Evitar alterações incompatíveis em contratos existentes sem planejamento.

## 6. Regras de negócio

Antes de implementar uma regra:

- Identificar sua finalidade.
- Consultar os requisitos.
- Identificar condições e exceções.
- Verificar dependências com outros módulos.
- Identificar permissões necessárias.
- Considerar consistência dos dados.

As regras de negócio devem ser implementadas em uma camada apropriada, respeitando a arquitetura do sistema.

Não inventar comportamentos ou decisões empresariais.

Quando houver ambiguidade, registrar a dúvida e solicitar esclarecimento.

## 7. Bancos de dados

Ao trabalhar com persistência:

- Identificar o banco de dados utilizado.
- Consultar o esquema existente.
- Respeitar relacionamentos e restrições.
- Utilizar consultas parametrizadas ou mecanismos seguros do framework.
- Considerar integridade referencial.
- Evitar consultas desnecessariamente custosas.
- Avaliar índices quando necessário.
- Tratar transações adequadamente.
- Evitar exposição de dados sensíveis.

### Alterações estruturais

Antes de modificar tabelas, colunas, índices ou relacionamentos:

1. Analisar o impacto.
2. Verificar dependências.
3. Avaliar compatibilidade com dados existentes.
4. Considerar migrations e rollback.
5. Identificar possíveis riscos de perda de dados.

Não executar migrations destrutivas sem autorização explícita.

## 8. Autenticação e autorização

Avaliar:

- Identificação dos usuários.
- Validação de credenciais.
- Gerenciamento de sessões ou tokens.
- Expiração e renovação de credenciais.
- Controle de acesso por perfil.
- Permissões por recurso.
- Proteção de rotas.
- Tratamento de tentativas inválidas.

Diferenciar autenticação de autorização.

Nunca considerar uma restrição implementada somente no front-end como mecanismo suficiente de segurança.

## 9. Segurança

Aplicar princípios de desenvolvimento seguro:

- Validar entradas.
- Sanitizar dados quando apropriado.
- Evitar SQL Injection.
- Prevenir exposição de informações sensíveis.
- Proteger credenciais.
- Utilizar variáveis de ambiente para segredos.
- Configurar CORS adequadamente.
- Aplicar controle de acesso.
- Considerar proteção contra CSRF quando aplicável.
- Avaliar riscos de dependências.
- Evitar mensagens de erro que exponham detalhes internos.
- Registrar eventos relevantes sem armazenar segredos.

Não desabilitar proteções de segurança apenas para contornar erros.

## 10. Integrações externas

Antes de integrar serviços:

1. Consultar a documentação oficial disponível.
2. Identificar métodos de autenticação.
3. Verificar parâmetros e contratos.
4. Avaliar limites de requisição.
5. Tratar timeouts.
6. Implementar tratamento de falhas.
7. Considerar retentativas quando apropriado.
8. Evitar processamento duplicado.
9. Proteger credenciais.
10. Testar o comportamento de integração.

Não afirmar que uma integração está operacional sem validação.

## 11. Tratamento de erros e logs

- Utilizar tratamento consistente de exceções.
- Evitar interrupções inesperadas.
- Registrar informações úteis para diagnóstico.
- Não registrar senhas, tokens ou dados confidenciais.
- Diferenciar erros de validação, autenticação, autorização e processamento.
- Evitar ocultar erros relevantes.
- Fornecer respostas adequadas ao consumidor da API.

## 12. Testes e validação

Executar, conforme a estrutura do projeto:

- Testes unitários.
- Testes de integração.
- Testes de API.
- Testes de autenticação e autorização.
- Testes de regras de negócio.
- Testes de persistência.
- Lint.
- Verificação de tipos.
- Build ou compilação.

Considerar cenários de sucesso, falha e casos extremos.

Não afirmar que uma validação foi executada sem evidências.

## 13. Gerenciamento de dependências

Antes de adicionar ou atualizar dependências:

1. Verificar as bibliotecas existentes.
2. Avaliar a necessidade real.
3. Conferir compatibilidade.
4. Considerar manutenção e segurança.
5. Avaliar impactos no projeto.

Não atualizar dependências indiscriminadamente.

## 14. Colaboração e Git

- Verificar o estado do Git antes das alterações.
- Preservar trabalho de outros integrantes.
- Respeitar branches e convenções.
- Evitar alterações fora do escopo.
- Comunicar mudanças que afetem contratos de API.
- Não realizar commit, push, merge ou operações destrutivas sem autorização.

## 15. Documentação

Manter documentação coerente com a implementação:

- Arquitetura.
- Endpoints.
- Contratos de API.
- Regras de negócio.
- Modelos e entidades.
- Banco de dados.
- Autenticação e autorização.
- Configurações.
- Variáveis de ambiente.
- Instalação e execução.
- Testes e validações.

Nunca documentar funcionalidades fictícias como se estivessem implementadas.

## 16. Fluxo de execução

Para cada tarefa:

1. Analisar o requisito.
2. Inspecionar a arquitetura.
3. Identificar os arquivos envolvidos.
4. Avaliar impactos e riscos.
5. Planejar a implementação.
6. Desenvolver a solução.
7. Executar testes e validações.
8. Revisar as alterações.
9. Atualizar a documentação quando necessário.
10. Apresentar os resultados.

## 17. Relatório final

Ao concluir, apresentar:

- Objetivo da implementação.
- Arquivos criados ou modificados.
- Endpoints afetados, quando aplicável.
- Alterações em regras de negócio.
- Alterações no banco de dados.
- Testes executados.
- Resultados das validações.
- Pendências e limitações.

## 18. Princípio fundamental

Desenvolver aplicações back-end seguras, confiáveis, organizadas e sustentáveis.

Toda implementação deve respeitar os requisitos reais, a arquitetura existente, a integridade dos dados e as regras específicas do projeto.