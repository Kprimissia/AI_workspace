# Workflow — Otimização de Desempenho

## Objetivo

Orientar o agente na análise e otimização do desempenho de aplicações, identificando gargalos e implementando melhorias fundamentadas em evidências, sem comprometer funcionalidades, segurança ou estabilidade.

## 1. Compreender o problema

Antes de realizar alterações:

- Identificar os sintomas de lentidão.
- Compreender quando e onde ocorrem.
- Identificar os usuários e funcionalidades afetados.
- Verificar se o problema é recorrente ou pontual.
- Identificar mudanças recentes que possam ter causado a degradação.
- Definir o resultado esperado.

Não presumir que um código é lento sem evidências.

## 2. Analisar a arquitetura

Inspecionar os componentes relevantes:

- Interface e renderização.
- Aplicação e lógica de negócio.
- APIs e comunicação entre sistemas.
- Banco de dados.
- Consultas e operações de leitura e escrita.
- Processamento em segundo plano.
- Dependências externas.
- Infraestrutura e ambiente de execução.

Identificar possíveis gargalos e suas relações.

## 3. Medir o desempenho atual

Sempre que possível, estabelecer uma referência antes das alterações.

Avaliar métricas como:

- Tempo de resposta.
- Latência.
- Tempo de carregamento.
- Uso de CPU.
- Consumo de memória.
- Volume de requisições.
- Tempo de consultas ao banco.
- Taxa de erros.
- Throughput.
- Tamanho dos arquivos enviados ao navegador.

Utilizar ferramentas de análise e monitoramento disponíveis no projeto.

Não inventar métricas ou resultados.

## 4. Identificar gargalos

Investigar possíveis problemas:

### Front-end
- Renderizações desnecessárias.
- Componentes excessivamente complexos.
- Carregamento de recursos pesados.
- Imagens sem otimização.
- JavaScript excessivo.
- Requisições redundantes.
- Ausência de estratégias adequadas de cache.
- Listas grandes sem virtualização quando necessária.

### Back-end
- Processamento desnecessário.
- Operações bloqueantes.
- Consultas ineficientes.
- Ausência de paginação.
- Requisições externas lentas.
- Consumo excessivo de memória.
- Falta de cache quando justificável.

### Banco de dados
- Consultas lentas.
- Índices ausentes ou inadequados.
- Consultas repetitivas.
- Problemas de relacionamento.
- Carregamento excessivo de registros.
- Operações desnecessárias.

## 5. Priorizar melhorias

Avaliar cada oportunidade considerando:

- Impacto no usuário.
- Frequência do problema.
- Gravidade do gargalo.
- Custo de implementação.
- Risco de regressão.
- Complexidade de manutenção.

Priorizar problemas comprovados e melhorias com benefício mensurável.

## 6. Planejar as alterações

Antes de implementar:

1. Descrever o gargalo identificado.
2. Apresentar evidências.
3. Identificar os arquivos e componentes envolvidos.
4. Propor uma solução.
5. Avaliar riscos.
6. Definir como medir o resultado.

Evitar otimizações prematuras.

## 7. Implementar melhorias

Durante a implementação:

- Preservar o comportamento esperado.
- Evitar complexidade desnecessária.
- Reduzir operações redundantes.
- Melhorar consultas quando necessário.
- Utilizar carregamento sob demanda quando adequado.
- Aplicar cache com critérios claros.
- Otimizar recursos estáticos.
- Evitar dependências desnecessárias.
- Respeitar a arquitetura existente.

Não aplicar técnicas de otimização sem compreender seus impactos.

## 8. Validar os resultados

Após as alterações:

- Executar testes disponíveis.
- Comparar métricas antes e depois.
- Verificar se o gargalo foi reduzido.
- Avaliar consumo de recursos.
- Verificar funcionalidades relacionadas.
- Identificar possíveis regressões.
- Confirmar que a melhoria não prejudicou a segurança.

Se não for possível medir o resultado, informar essa limitação.

## 9. Documentar

Registrar:

- Problema identificado.
- Evidências coletadas.
- Métricas anteriores.
- Melhorias realizadas.
- Arquivos modificados.
- Métricas posteriores.
- Testes executados.
- Limitações e recomendações.

## 10. Git e colaboração

- Preservar alterações de outros integrantes.
- Evitar modificar arquivos fora do escopo.
- Não sobrescrever otimizações existentes.
- Não executar operações destrutivas sem autorização.
- Não realizar commit, push, merge ou publicação sem autorização explícita.

## 11. Relatório final

Apresentar:

- Problema de desempenho.
- Causa identificada.
- Evidências e métricas.
- Melhorias implementadas.
- Arquivos modificados.
- Testes realizados.
- Comparação de resultados.
- Riscos e limitações.
- Recomendações futuras.

## Regras obrigatórias

1. Medir antes de otimizar sempre que possível.
2. Não inventar gargalos ou resultados.
3. Não comprometer funcionalidades por desempenho.
4. Priorizar melhorias fundamentadas em evidências.
5. Evitar otimizações prematuras.
6. Preservar segurança e estabilidade.
7. Não realizar alterações de infraestrutura ou produção sem autorização.
8. Informar claramente quando não for possível validar os ganhos.