# Workflow — Resposta a Incidentes e Recuperação de Sistemas

## Objetivo

Orientar o agente na identificação, investigação, contenção, resolução e documentação de incidentes técnicos, minimizando impactos sobre usuários, dados e operações do sistema.

## 1. Identificar o incidente

Ao receber um relato de incidente:

- Compreender o problema informado.
- Identificar quando começou.
- Identificar os sistemas e funcionalidades afetados.
- Verificar se o problema é recorrente.
- Identificar a quantidade de usuários potencialmente afetados.
- Avaliar se existe risco de perda ou exposição de dados.
- Consultar incidentes anteriores, quando disponíveis.

Não presumir a causa antes de investigar.

## 2. Classificar a gravidade

Utilizar uma classificação proporcional ao impacto:

- **CRÍTICO:** sistema indisponível, comprometimento de segurança ou risco grave à integridade dos dados.
- **ALTO:** funcionalidade essencial comprometida ou impacto significativo sobre usuários.
- **MÉDIO:** falha localizada com alternativa temporária disponível.
- **BAIXO:** problema de impacto limitado, sem comprometimento relevante das operações.

Registrar a justificativa da classificação.

## 3. Investigar o problema

Analisar:

- Logs da aplicação.
- Métricas de desempenho.
- Histórico de alterações.
- Estado dos serviços.
- Conectividade.
- Banco de dados.
- Integrações externas.
- Configurações.
- Dependências.
- Mensagens de erro.

Correlacionar os eventos para identificar a origem provável.

Diferenciar fatos confirmados de hipóteses.

## 4. Avaliar os impactos

Identificar:

- Funcionalidades indisponíveis.
- Usuários afetados.
- Operações interrompidas.
- Dados potencialmente comprometidos.
- Integrações afetadas.
- Riscos de propagação.
- Consequências operacionais.

Priorizar a proteção dos usuários e da integridade dos dados.

## 5. Conter o incidente

Quando necessário, propor medidas para limitar o impacto:

- Desabilitar temporariamente uma funcionalidade comprometida.
- Isolar um serviço afetado.
- Interromper operações inseguras.
- Restringir acessos.
- Suspender integrações com falhas.
- Preservar evidências técnicas.

A execução de ações que afetem usuários, serviços ou produção exige autorização explícita.

Não apagar logs ou evidências durante a investigação.

## 6. Planejar a recuperação

Antes de corrigir:

1. Identificar a causa provável.
2. Definir a estratégia de recuperação.
3. Identificar os componentes envolvidos.
4. Avaliar riscos de regressão.
5. Verificar backups disponíveis, quando necessário.
6. Definir os critérios de recuperação.
7. Estabelecer uma estratégia de rollback.

Não presumir que um backup existe ou está íntegro sem verificar.

## 7. Corrigir o problema

Durante a recuperação:

- Corrigir a causa identificada.
- Evitar alterações fora do escopo.
- Preservar dados.
- Manter compatibilidade com os módulos relacionados.
- Aplicar correções de segurança quando necessárias.
- Registrar alterações relevantes.
- Evitar soluções temporárias sem documentar suas limitações.

Não executar operações destrutivas sem autorização.

## 8. Validar a recuperação

Após a correção:

- Verificar disponibilidade dos serviços.
- Testar funcionalidades afetadas.
- Validar integrações.
- Verificar integridade dos dados.
- Consultar logs recentes.
- Avaliar métricas.
- Verificar se o problema não voltou a ocorrer.
- Confirmar se os critérios de recuperação foram atendidos.

Não considerar o incidente resolvido apenas porque a mensagem de erro desapareceu.

## 9. Comunicar o incidente

Preparar informações claras para os responsáveis:

- O que aconteceu.
- Quando começou.
- Quais sistemas foram afetados.
- Qual foi o impacto.
- O que está sendo feito.
- Quais riscos permanecem.
- Qual é a situação atual.

Não divulgar informações sensíveis ou detalhes técnicos restritos a pessoas não autorizadas.

## 10. Documentar o incidente

Registrar:

- Identificador do incidente.
- Data e horário.
- Descrição.
- Classificação.
- Sistemas afetados.
- Evidências.
- Linha do tempo.
- Causa identificada ou hipótese.
- Medidas de contenção.
- Correções realizadas.
- Resultado da recuperação.
- Pendências.

## 11. Análise posterior

Após a resolução:

- Identificar a causa raiz, quando possível.
- Avaliar por que o problema não foi detectado anteriormente.
- Identificar falhas de prevenção.
- Avaliar a eficácia da resposta.
- Propor melhorias.
- Definir ações preventivas.
- Identificar necessidades de monitoramento ou testes adicionais.

Priorizar aprendizado e prevenção, evitando atribuir culpa sem evidências.

## 12. Git e colaboração

- Preservar evidências e alterações existentes.
- Não sobrescrever trabalho de outros integrantes.
- Não reverter alterações sem compreender seus impactos.
- Não executar comandos destrutivos sem autorização.
- Não realizar commit, push, merge ou publicação sem autorização explícita.
- Comunicar riscos críticos aos responsáveis.

## 13. Relatório final

Apresentar:

- Identificação do incidente.
- Gravidade.
- Descrição do problema.
- Impactos.
- Causa identificada.
- Medidas de contenção.
- Correções realizadas.
- Testes executados.
- Situação atual.
- Riscos residuais.
- Ações preventivas recomendadas.

## Regras obrigatórias

1. Priorizar a segurança dos usuários e dos dados.
2. Não presumir causas sem evidências.
3. Preservar logs e evidências.
4. Não executar ações em produção sem autorização.
5. Não realizar operações destrutivas sem autorização.
6. Verificar a integridade dos dados durante a recuperação.
7. Não afirmar que o incidente foi resolvido sem validação.
8. Comunicar incidentes críticos aos responsáveis.
9. Documentar decisões e ações realizadas.
10. Priorizar medidas que evitem a recorrência do problema.