---
name: code-review
description: Realiza revisões técnicas de código em busca de bugs, vulnerabilidades, falhas de lógica, problemas de arquitetura, regressões e violações de boas práticas. Utilize esta skill para revisar alterações, commits, branches, Pull Requests e implementações completas.
---

# Code Review

## 1. Objetivo

Estabelecer um procedimento sistemático para revisar código-fonte, identificar problemas técnicos e avaliar a qualidade das implementações.

A revisão deve priorizar a identificação de defeitos reais, riscos e impactos sobre o funcionamento do sistema.

O objetivo não é apenas encontrar problemas, mas fornecer recomendações fundamentadas que contribuam para a evolução do projeto.

## 2. Escopo

Esta Skill pode ser utilizada para revisar:

- Código novo.
- Código existente.
- Commits.
- Branches.
- Pull Requests.
- Componentes.
- Serviços.
- APIs.
- Testes automatizados.
- Configurações.
- Documentação técnica relacionada à implementação.

A análise deve respeitar as tecnologias e a arquitetura identificadas no projeto.

## 3. Preparação da revisão e sincronização obrigatória

Antes de iniciar:

1. Identificar o projeto e seu contexto.
2. **Sincronizar obrigatoriamente o repositório com o remoto (`git fetch --all --prune`), atualizando `main` e `develop` e comparando `origin/main` vs `origin/develop`** para identificar todas as entregas recentes e eventuais sobrescritas de código em merges.
3. Consultar as instruções disponíveis, especialmente `AGENTS.md`.
3. Identificar o objetivo da alteração.
4. Analisar os arquivos envolvidos.
5. Verificar o estado do Git.
6. Identificar a branch de origem e o destino da alteração, quando aplicável.
7. Consultar requisitos e critérios de aceite.
8. Identificar dependências e funcionalidades relacionadas.

Não avaliar uma implementação sem considerar seu contexto.

## 4. Categorias de análise

### 4.1. Funcionamento e lógica

Verificar:

- Condições incorretas.
- Erros de lógica.
- Fluxos incompletos.
- Valores inesperados.
- Problemas de estado.
- Tratamento inadequado de exceções.
- Comportamentos inconsistentes.
- Falhas em casos extremos.

### 4.2. Arquitetura e organização

Avaliar:

- Separação de responsabilidades.
- Acoplamento excessivo.
- Duplicação de código.
- Organização de módulos.
- Reutilização adequada.
- Consistência com a arquitetura existente.
- Complexidade desnecessária.
- Dependências inadequadas.

### 4.3. Segurança

Verificar, conforme o contexto:

- Exposição de credenciais.
- Falhas de autenticação.
- Falhas de autorização.
- Validação inadequada de entradas.
- Exposição indevida de dados.
- Vulnerabilidades relacionadas a dependências.
- Configurações inseguras.
- Manipulação inadequada de informações sensíveis.

Não afirmar a existência de uma vulnerabilidade sem apresentar evidências suficientes.

### 4.4. Desempenho

Avaliar:

- Operações desnecessárias.
- Processamento excessivo.
- Consultas ineficientes.
- Chamadas repetidas.
- Renderizações desnecessárias.
- Uso inadequado de recursos.
- Problemas de escalabilidade.

Considerar o impacto real antes de recomendar otimizações.

### 4.5. Qualidade e manutenção

Verificar:

- Legibilidade.
- Nomenclatura.
- Padronização.
- Tipagem.
- Tratamento de erros.
- Complexidade.
- Testabilidade.
- Facilidade de manutenção.

Diferenciar problemas funcionais de preferências de estilo.

### 4.6. Testes

Avaliar:

- Existência de testes relevantes.
- Cobertura de cenários importantes.
- Casos de sucesso.
- Casos de falha.
- Casos extremos.
- Testes de regressão.
- Coerência entre testes e requisitos.

Não considerar a simples existência de testes como garantia de qualidade.

## 5. Análise de alterações

Quando revisar um conjunto de mudanças:

1. Identificar os arquivos alterados.
2. Examinar o diff completo.
3. Compreender a finalidade de cada alteração.
4. Identificar dependências entre arquivos.
5. Avaliar impactos em funcionalidades existentes.
6. Procurar problemas introduzidos pelas mudanças.
7. Verificar se os critérios de aceite foram atendidos.

Priorizar problemas introduzidos pela alteração analisada.

Não atribuir automaticamente à alteração problemas preexistentes sem diferenciá-los.

## 6. Classificação de severidade

Classificar os achados de acordo com seu impacto:

### CRITICAL
Problemas que representam risco grave à segurança, integridade dos dados ou funcionamento essencial do sistema.

### HIGH
Problemas que podem causar falhas importantes, comprometer funcionalidades centrais ou gerar impactos significativos.

### MEDIUM
Problemas que afetam funcionalidades específicas, confiabilidade ou manutenção, mas possuem impacto mais limitado.

### LOW
Problemas de menor impacto, melhorias pontuais ou inconsistências que não comprometem diretamente o funcionamento.

### INFO
Observações, sugestões e oportunidades de melhoria que não representam necessariamente defeitos.

A severidade deve ser fundamentada no impacto e na probabilidade, não apenas na preferência técnica do revisor.

## 7. Estrutura de apresentação dos achados

Cada problema identificado deve apresentar:

**Severidade:** classificação do problema.

**Localização:** arquivo e linha ou trecho relevante.

**Problema:** descrição objetiva do que está errado.

**Impacto:** consequência possível para o sistema.

**Evidência:** trecho de código, fluxo ou comportamento que fundamenta a observação.

**Recomendação:** proposta de correção.

Quando não houver problemas identificados, informar que nenhum achado foi encontrado no escopo analisado. Não declarar que o sistema está livre de defeitos.

## 8. Diretrizes de revisão

- Priorizar achados relevantes.
- Evitar apontamentos vagos.
- Não inventar problemas.
- Não confundir preferência pessoal com defeito.
- Não recomendar refatorações sem benefício justificável.
- Considerar compatibilidade com o restante do projeto.
- Apresentar evidências para cada apontamento.
- Diferenciar problemas confirmados de suspeitas que precisam de investigação.
- Não alterar o código durante uma revisão, salvo quando a correção também tiver sido solicitada.

## 9. Validação técnica

Quando autorizado e possível:

- Executar testes automatizados.
- Executar lint.
- Executar verificação de tipos.
- Executar build.
- Reproduzir o problema identificado.
- Verificar os resultados das correções.

Registrar quais verificações foram efetivamente executadas.

A análise estática não substitui testes de execução.

## 10. Revisão de Pull Requests

Ao revisar um Pull Request:

1. Consultar sua descrição.
2. Identificar a Issue relacionada.
3. Conferir o objetivo da alteração.
4. Examinar os arquivos modificados.
5. Analisar o diff.
6. Verificar testes e validações.
7. Identificar regressões e riscos.
8. Apresentar os achados organizados por severidade.

Não aprovar, rejeitar ou realizar merge automaticamente.

## 11. Proteção do projeto

Durante a revisão:

- Não modificar arquivos sem autorização.
- Não descartar alterações locais.
- Não executar operações destrutivas.
- Não alterar branches compartilhadas.
- Preservar o trabalho de outros integrantes.
- Não expor informações confidenciais.

## 12. Relatório final

Ao concluir uma revisão, apresentar:

### Resumo executivo
Avaliação geral do escopo analisado.

### Achados
Lista de problemas identificados, classificados por severidade.

### Validações
Testes e verificações executados.

### Riscos
Pontos que exigem atenção ou investigação adicional.

### Recomendações
Correções e melhorias prioritárias.

### Conclusão
Informar se foram encontrados bloqueios técnicos no escopo analisado.

## 13. Princípio fundamental

Uma boa revisão deve ser objetiva, fundamentada e orientada à prevenção de problemas.

O agente deve agir como um revisor técnico criterioso, não como alguém que procura defeitos artificiais para justificar sua análise.

A prioridade é proteger a qualidade, a segurança e a confiabilidade do software.