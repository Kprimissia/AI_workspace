# Workflow — Monitoramento, Logs e Diagnóstico

## Objetivo

Orientar o agente na análise, implementação e manutenção de mecanismos de monitoramento, registros de eventos e diagnóstico de aplicações, facilitando a identificação de falhas, a investigação de incidentes e o acompanhamento da saúde do sistema.

## 1. Compreender o ambiente

Antes de iniciar:

- Identificar a arquitetura da aplicação.
- Verificar as tecnologias utilizadas.
- Identificar os ambientes de execução.
- Consultar os mecanismos de logs existentes.
- Verificar ferramentas de monitoramento disponíveis.
- Identificar os principais serviços e dependências.
- Compreender quais funcionalidades são críticas.

Não presumir que ferramentas ou serviços de monitoramento estão instalados.

## 2. Inspecionar os mecanismos existentes

Verificar:

- Configuração de logs.
- Formato dos registros.
- Níveis de log.
- Tratamento de exceções.
- Monitoramento de serviços.
- Métricas disponíveis.
- Alertas configurados.
- Rastreamento de requisições.
- Histórico de falhas.
- Integrações com ferramentas externas.

Preservar os padrões já utilizados pelo projeto.

## 3. Analisar os logs

Investigar registros relacionados a:

- Erros de execução.
- Falhas de autenticação.
- Falhas de autorização.
- Requisições HTTP.
- Erros de integração.
- Problemas de banco de dados.
- Falhas de processamento.
- Indisponibilidade de serviços.
- Eventos relevantes para auditoria.

Considerar o contexto e a sequência temporal dos eventos.

Não concluir que um registro isolado representa a causa de um problema sem investigar as evidências.

## 4. Definir níveis de log

Utilizar níveis adequados ao propósito dos registros:

- **DEBUG:** informações detalhadas para investigação durante o desenvolvimento.
- **INFO:** eventos normais e relevantes da aplicação.
- **WARN:** situações inesperadas que não interrompem necessariamente o funcionamento.
- **ERROR:** falhas que impedem uma operação ou funcionalidade.
- **FATAL:** falhas críticas que comprometem a execução do sistema, quando suportado pela tecnologia.

Evitar registrar informações excessivas ou irrelevantes.

## 5. Garantir qualidade dos registros

Os logs devem:

- Ter mensagens claras.
- Identificar o evento ocorrido.
- Incluir contexto técnico relevante.
- Utilizar timestamps adequados.
- Facilitar a correlação de eventos.
- Evitar mensagens ambíguas.
- Permitir identificar a origem da falha.
- Manter consistência de formato.

Quando apropriado, utilizar logs estruturados.

## 6. Proteger informações sensíveis

Nunca registrar diretamente:

- Senhas.
- Tokens de autenticação.
- Chaves de API.
- Credenciais de banco de dados.
- Dados pessoais desnecessários.
- Informações financeiras sensíveis.
- Conteúdo privado de usuários sem necessidade legítima.

Aplicar mascaramento ou anonimização quando necessário.

Respeitar os requisitos de proteção de dados e a LGPD.

## 7. Monitorar a aplicação

Avaliar métricas relevantes, conforme a arquitetura:

### Aplicação
- Taxa de erros.
- Tempo de resposta.
- Volume de requisições.
- Disponibilidade.
- Operações concluídas e falhas.

### Infraestrutura
- Uso de CPU.
- Consumo de memória.
- Espaço em disco.
- Disponibilidade de serviços.
- Recursos de rede.

### Banco de dados
- Tempo de consultas.
- Conexões ativas.
- Falhas de conexão.
- Consumo de recursos.
- Operações lentas.

Não implementar métricas sem finalidade de monitoramento definida.

## 8. Configurar alertas

Quando houver suporte:

- Identificar eventos críticos.
- Definir condições de alerta.
- Evitar notificações excessivas.
- Priorizar falhas com impacto real.
- Definir responsáveis pelo acompanhamento.
- Registrar procedimentos de resposta.
- Validar se os alertas funcionam.

Não criar alertas sem compreender seus critérios e consequências.

## 9. Investigar incidentes

Quando ocorrer uma falha:

1. Identificar o sintoma.
2. Determinar quando começou.
3. Identificar usuários e funcionalidades afetados.
4. Consultar logs e métricas.
5. Correlacionar eventos.
6. Verificar alterações recentes.
7. Investigar dependências externas.
8. Identificar a causa provável.
9. Propor correção.
10. Validar a recuperação.

Diferenciar causa confirmada de hipótese investigativa.

## 10. Melhorar o diagnóstico

Quando necessário:

- Adicionar logs em pontos críticos.
- Melhorar mensagens de erro.
- Implementar identificadores de correlação.
- Registrar eventos relevantes.
- Melhorar o tratamento de exceções.
- Reduzir registros duplicados.
- Corrigir informações insuficientes.

Evitar utilizar logs como substitutos de testes ou validações adequadas.

## 11. Validar as alterações

Após implementar melhorias:

- Verificar se os registros são gerados corretamente.
- Confirmar que os níveis de log são adequados.
- Verificar se informações sensíveis não aparecem.
- Testar cenários de erro.
- Validar métricas.
- Testar alertas, quando existentes.
- Verificar possíveis impactos no desempenho.

Não afirmar que o monitoramento está funcionando sem realizar verificações.

## 12. Documentar

Registrar:

- Ferramentas utilizadas.
- Configurações de monitoramento.
- Níveis de log.
- Métricas acompanhadas.
- Alertas configurados.
- Procedimentos de diagnóstico.
- Localização dos registros.
- Restrições e limitações.
- Procedimentos de resposta a incidentes.

Não documentar credenciais ou informações secretas.

## 13. Git e colaboração

- Preservar configurações existentes.
- Não sobrescrever alterações de outros integrantes.
- Evitar versionar logs reais ou dados sensíveis.
- Não modificar infraestrutura sem autorização.
- Não executar operações destrutivas sem autorização.
- Não realizar commit, push, merge ou publicação sem autorização explícita.

## 14. Relatório final

Apresentar:

- Ambiente analisado.
- Problemas identificados.
- Evidências consultadas.
- Melhorias implementadas.
- Arquivos modificados.
- Métricas e logs avaliados.
- Testes executados.
- Resultados.
- Riscos e limitações.
- Recomendações futuras.

## Regras obrigatórias

1. Utilizar evidências para investigar falhas.
2. Não inventar eventos ou métricas.
3. Não expor informações sensíveis nos logs.
4. Evitar registros excessivos.
5. Diferenciar hipóteses de causas confirmadas.
6. Preservar o desempenho da aplicação.
7. Respeitar a arquitetura e as ferramentas existentes.
8. Não modificar ambientes de produção sem autorização.
9. Documentar limitações do monitoramento.
10. Não afirmar que um sistema está monitorado sem verificar os mecanismos existentes.