# Workflow — Refatoração e Melhoria de Código

## Objetivo

Orientar o agente na refatoração de código existente, melhorando organização, legibilidade, manutenção, desempenho e arquitetura sem alterar indevidamente o comportamento esperado do sistema.

## 1. Entender a necessidade

Antes de modificar qualquer código:

- Identificar o problema que motivou a refatoração.
- Entender o comportamento atual.
- Identificar o resultado esperado.
- Verificar se existem requisitos ou restrições específicas.
- Identificar os arquivos e módulos envolvidos.

Não refatorar apenas por preferência pessoal ou por questões estéticas.

## 2. Analisar o estado atual

Inspecionar:

- Estrutura do projeto.
- Arquivos envolvidos.
- Dependências e integrações.
- Padrões utilizados no restante do código.
- Testes existentes.
- Histórico recente de alterações, quando relevante.
- Estado atual do Git.

Identificar possíveis riscos de regressão antes de começar.

## 3. Identificar oportunidades de melhoria

Avaliar:

- Código duplicado.
- Funções excessivamente grandes.
- Responsabilidades misturadas.
- Acoplamento desnecessário.
- Nomes pouco claros.
- Complexidade excessiva.
- Componentes ou módulos difíceis de manter.
- Dependências desnecessárias.
- Problemas de organização e arquitetura.
- Oportunidades de melhorar testes.

Priorizar melhorias que tragam benefícios reais.

## 4. Planejar a refatoração

Antes de executar:

1. Listar os arquivos que serão modificados.
2. Descrever as melhorias propostas.
3. Identificar possíveis impactos.
4. Definir como preservar o comportamento existente.
5. Determinar quais testes serão necessários.

Em refatorações extensas, dividir o trabalho em etapas pequenas e verificáveis.

## 5. Executar as alterações

Durante a implementação:

- Preservar as funcionalidades existentes.
- Seguir os padrões já adotados pelo projeto.
- Evitar alterações fora do escopo.
- Não duplicar soluções existentes.
- Não adicionar dependências sem justificativa.
- Manter compatibilidade com os módulos relacionados.
- Evitar mudanças simultâneas desnecessárias.
- Não remover funcionalidades sem autorização.

A refatoração deve melhorar a estrutura interna sem provocar mudanças funcionais não solicitadas.

## 6. Validar o comportamento

Após cada etapa relevante:

- Executar os testes disponíveis.
- Verificar funcionalidades afetadas.
- Executar lint e verificação de tipos, quando disponíveis.
- Executar o build, quando aplicável.
- Verificar integrações e dependências.
- Comparar o comportamento antes e depois.

Se algum teste falhar, investigar a causa antes de considerar a refatoração concluída.

## 7. Revisar as alterações

Analisar o diff e verificar:

- Se todas as alterações são necessárias.
- Se o comportamento original foi preservado.
- Se surgiram regressões.
- Se existem alterações acidentais.
- Se a nova implementação está mais clara e sustentável.
- Se os padrões do projeto foram respeitados.

## 8. Documentar

Atualizar a documentação somente quando a refatoração alterar informações relevantes, como:

- Arquitetura.
- Organização dos módulos.
- Responsabilidades de componentes.
- Fluxos internos.
- Configurações.
- Dependências.

Não criar documentação desnecessária.

## 9. Git e colaboração

- Preservar alterações de outros desenvolvedores.
- Não sobrescrever trabalho de terceiros.
- Não executar comandos destrutivos sem autorização.
- Não realizar commit, push, merge ou publicação sem autorização explícita.
- Quando autorizado, utilizar commits pequenos e descritivos.

## 10. Relatório final

Apresentar:

- Objetivo da refatoração.
- Problemas identificados.
- Melhorias realizadas.
- Arquivos modificados.
- Testes executados.
- Resultados das validações.
- Riscos ou pendências.
- Sugestões de melhorias futuras.

## Regras obrigatórias

1. Preservar o comportamento existente, salvo solicitação contrária.
2. Não alterar funcionalidades fora do escopo.
3. Não refatorar sem compreender o código atual.
4. Não introduzir complexidade desnecessária.
5. Não remover código apenas por parecer inútil sem verificar suas dependências.
6. Não afirmar que a refatoração está validada sem executar as verificações disponíveis.
7. Priorizar segurança, estabilidade e manutenção do projeto.