# Workflow — Gerenciamento de Banco de Dados

## Objetivo

Orientar o agente na análise, criação, manutenção e otimização de bancos de dados, garantindo integridade, segurança, consistência e compatibilidade com a aplicação.

## 1. Compreender a necessidade

Antes de realizar alterações:

- Identificar o objetivo da mudança.
- Compreender as entidades e os dados envolvidos.
- Identificar os módulos que dependem dessas informações.
- Verificar se a estrutura já atende à necessidade.
- Identificar regras de negócio relacionadas.
- Avaliar impactos em funcionalidades existentes.

Não criar tabelas ou campos sem compreender sua finalidade.

## 2. Inspecionar o ambiente

Identificar:

- Sistema gerenciador de banco de dados (SGBD).
- Versão utilizada.
- Estrutura atual.
- Tabelas e relacionamentos.
- Chaves primárias e estrangeiras.
- Índices.
- Restrições.
- Views, procedures e triggers, quando existentes.
- Mecanismo de migrations.
- Configurações de conexão.

Não presumir tecnologias ou versões. Consultar os arquivos e configurações do projeto.

## 3. Analisar a modelagem

Avaliar:

- Entidades e atributos.
- Relacionamentos.
- Cardinalidade.
- Chaves primárias.
- Chaves estrangeiras.
- Restrições de integridade.
- Normalização.
- Tipos de dados.
- Campos obrigatórios e opcionais.
- Regras de exclusão e atualização.

Evitar duplicidade de informações e estruturas desnecessariamente complexas.

## 4. Planejar alterações

Antes de modificar o banco:

1. Identificar as estruturas afetadas.
2. Avaliar dependências.
3. Verificar compatibilidade com a aplicação.
4. Identificar riscos de perda ou inconsistência de dados.
5. Definir a estratégia de alteração.
6. Planejar migrations e rollback, quando aplicável.
7. Definir os testes necessários.

Alterações destrutivas exigem autorização explícita.

## 5. Implementar alterações

Durante a implementação:

- Utilizar o mecanismo de migrations do projeto.
- Manter histórico das alterações estruturais.
- Definir tipos de dados adequados.
- Criar restrições de integridade.
- Utilizar relacionamentos consistentes.
- Evitar alterações manuais não documentadas.
- Preservar compatibilidade com a aplicação.
- Evitar duplicação de estruturas.
- Considerar impacto em dados existentes.

Não executar migrations diretamente em produção sem autorização.

## 6. Consultas e operações

Ao criar ou modificar consultas:

- Utilizar consultas parametrizadas.
- Evitar SQL Injection.
- Selecionar apenas os campos necessários.
- Evitar consultas redundantes.
- Avaliar índices quando necessário.
- Considerar paginação para grandes volumes.
- Utilizar transações quando apropriado.
- Garantir consistência nas operações relacionadas.

Não utilizar consultas destrutivas sem verificar seu impacto.

## 7. Segurança dos dados

Aplicar:

- Proteção das credenciais de conexão.
- Controle de acesso.
- Princípio do menor privilégio.
- Consultas parametrizadas.
- Proteção de informações pessoais.
- Separação entre ambientes.
- Controle de acesso a backups.
- Políticas adequadas de retenção.
- Proteção de dados conforme a LGPD.

Nunca inserir credenciais reais no código ou na documentação.

## 8. Integridade e consistência

Verificar:

- Chaves primárias e estrangeiras.
- Restrições de unicidade.
- Campos obrigatórios.
- Consistência entre relacionamentos.
- Transações.
- Regras de atualização e exclusão.
- Possibilidade de registros órfãos.
- Tratamento de operações parcialmente concluídas.

Não remover restrições de integridade apenas para fazer uma operação funcionar.

## 9. Testar as alterações

Executar, conforme aplicável:

- Testes de migrations.
- Testes de consultas.
- Testes de inserção e atualização.
- Testes de exclusão.
- Testes de relacionamentos.
- Testes de integridade.
- Testes de transações.
- Testes de compatibilidade com a aplicação.
- Testes de rollback.

Priorizar ambientes de desenvolvimento e teste.

Não utilizar dados reais de produção sem autorização.

## 10. Avaliar desempenho

Verificar:

- Consultas lentas.
- Índices ausentes ou inadequados.
- Operações repetitivas.
- Volume de dados retornados.
- Consultas desnecessariamente complexas.
- Problemas de concorrência.
- Uso excessivo de recursos.

Otimizar somente quando houver necessidade ou evidências de gargalos.

## 11. Backup e recuperação

Antes de alterações relevantes:

- Verificar a existência de backup.
- Confirmar se o procedimento de recuperação é conhecido.
- Avaliar riscos de perda de dados.
- Identificar dependências de recuperação.
- Planejar rollback.

Não afirmar que existe backup válido sem verificar.

## 12. Documentar

Registrar:

- SGBD e versão identificados.
- Estruturas criadas ou modificadas.
- Relacionamentos.
- Migrations.
- Consultas relevantes.
- Restrições.
- Configurações necessárias.
- Procedimentos de execução.
- Estratégia de recuperação.
- Limitações conhecidas.

## 13. Git e colaboração

- Versionar migrations e scripts necessários.
- Preservar alterações de outros integrantes.
- Não versionar dados sensíveis ou credenciais.
- Não sobrescrever migrations compartilhadas.
- Comunicar mudanças que afetem contratos entre sistemas.
- Não executar operações destrutivas sem autorização.
- Não realizar commit, push ou merge sem autorização explícita.

## 14. Relatório final

Apresentar:

- Objetivo da alteração.
- Estruturas analisadas.
- Alterações realizadas.
- Arquivos e migrations envolvidos.
- Impactos identificados.
- Testes executados.
- Resultados.
- Riscos e pendências.
- Recomendações.

## Regras obrigatórias

1. Nunca presumir a tecnologia do banco.
2. Preservar a integridade dos dados.
3. Não executar operações destrutivas sem autorização.
4. Utilizar migrations quando o projeto possuir esse mecanismo.
5. Proteger credenciais e informações sensíveis.
6. Utilizar consultas parametrizadas.
7. Avaliar compatibilidade com a aplicação.
8. Não executar alterações em produção sem autorização.
9. Verificar backup e recuperação quando necessário.
10. Não afirmar que uma alteração foi validada sem executar os testes disponíveis.