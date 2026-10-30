# Workflow — Integração com APIs e Serviços Externos

## Objetivo

Orientar o agente na análise, implementação, manutenção e validação de integrações entre aplicações, APIs e serviços externos, priorizando segurança, confiabilidade e compatibilidade.

## 1. Compreender a integração

Antes de implementar:

- Identificar o serviço ou sistema que será integrado.
- Compreender o objetivo da integração.
- Identificar os dados que serão enviados e recebidos.
- Verificar quais funcionalidades dependem da integração.
- Identificar os sistemas envolvidos.
- Verificar se a integração já existe no projeto.

Não implementar uma integração sem compreender seu propósito e seus limites.

## 2. Consultar a documentação

Priorizar a documentação oficial do serviço.

Investigar:

- Endereço-base da API.
- Endpoints disponíveis.
- Métodos HTTP.
- Parâmetros obrigatórios e opcionais.
- Formatos de requisição e resposta.
- Autenticação e autorização.
- Limites de requisições.
- Paginação.
- Códigos de status.
- Tratamento de erros.
- Webhooks, quando disponíveis.
- Restrições e limitações conhecidas.

Não inventar endpoints, parâmetros ou comportamentos.

## 3. Analisar a arquitetura existente

Verificar:

- Organização dos serviços de integração.
- Camada responsável pelas requisições.
- Configurações de ambiente.
- Tipagem dos dados.
- Tratamento centralizado de erros.
- Autenticação existente.
- Dependências utilizadas.
- Testes disponíveis.

Seguir os padrões do projeto e evitar criar mecanismos duplicados.

## 4. Definir o contrato da integração

Identificar:

- Dados enviados.
- Dados recebidos.
- Tipos e formatos.
- Campos obrigatórios.
- Regras de validação.
- Respostas esperadas.
- Possíveis falhas.
- Responsabilidades de cada sistema.

Quando necessário, documentar o contrato da integração antes de implementar.

## 5. Implementar a comunicação

Durante a implementação:

- Utilizar os métodos HTTP adequados.
- Respeitar os contratos documentados.
- Validar dados antes do envio.
- Tratar respostas de forma consistente.
- Configurar timeouts adequados.
- Considerar limites de requisições.
- Evitar chamadas desnecessárias.
- Implementar paginação quando aplicável.
- Evitar duplicação de lógica.
- Utilizar tipagem adequada quando suportada.

## 6. Proteger credenciais e dados

Aplicar obrigatoriamente:

- Não inserir tokens, senhas ou chaves diretamente no código.
- Utilizar variáveis de ambiente ou mecanismos seguros de configuração.
- Não versionar arquivos com credenciais reais.
- Não expor informações sensíveis em logs.
- Validar e controlar os dados recebidos.
- Aplicar autenticação e autorização adequadas.
- Utilizar HTTPS quando disponível.
- Respeitar os princípios de proteção de dados.

Credenciais reais nunca devem ser inventadas ou compartilhadas em exemplos.

## 7. Tratar erros e falhas

Considerar situações como:

- Falha de conexão.
- Timeout.
- Resposta inválida.
- Erros HTTP.
- Credenciais inválidas.
- Acesso não autorizado.
- Limite de requisições excedido.
- Serviço indisponível.
- Dados inconsistentes.

As falhas devem ser tratadas sem expor detalhes internos ou informações sensíveis.

Quando apropriado, utilizar:

- Retry com limites.
- Backoff progressivo.
- Idempotência.
- Logs estruturados.
- Monitoramento.
- Circuit breaker.

Não aplicar mecanismos complexos sem necessidade.

## 8. Implementar integrações assíncronas

Quando a integração envolver processamento em segundo plano:

- Identificar se o processamento precisa ser assíncrono.
- Avaliar filas e mecanismos de reprocessamento.
- Evitar processamento duplicado.
- Controlar o estado das operações.
- Registrar falhas.
- Definir critérios de tentativa e encerramento.
- Considerar idempotência.

## 9. Testar a integração

Executar, conforme aplicável:

- Testes unitários.
- Testes de integração.
- Testes com mocks.
- Testes de contrato.
- Testes de autenticação.
- Testes de erros.
- Testes de timeout.
- Testes de limites de requisição.
- Testes de dados inválidos.

Não utilizar serviços ou dados de produção sem autorização.

## 10. Validar o funcionamento

Verificar:

- Se a comunicação ocorre corretamente.
- Se os dados enviados respeitam o contrato.
- Se as respostas são interpretadas corretamente.
- Se os erros são tratados.
- Se as credenciais permanecem protegidas.
- Se não houve regressões.
- Se a integração funciona com os módulos relacionados.

## 11. Documentar

Registrar:

- Serviço integrado.
- Objetivo.
- Endpoints utilizados.
- Métodos HTTP.
- Contratos de dados.
- Configurações necessárias.
- Variáveis de ambiente, sem valores secretos.
- Regras de autenticação.
- Tratamento de erros.
- Limitações conhecidas.
- Procedimentos de teste.

## 12. Git e colaboração

- Preservar alterações de outros integrantes.
- Não sobrescrever implementações existentes.
- Não modificar contratos compartilhados sem avaliar os impactos.
- Comunicar dependências entre front-end e back-end.
- Não executar operações destrutivas sem autorização.
- Não realizar commit, push ou merge sem autorização explícita.

## 13. Relatório final

Apresentar:

- Serviço integrado.
- Objetivo da integração.
- Arquivos modificados.
- Endpoints utilizados.
- Configurações necessárias.
- Testes executados.
- Resultados.
- Limitações.
- Pendências e riscos.

## Regras obrigatórias

1. Priorizar a documentação oficial.
2. Não inventar contratos ou endpoints.
3. Nunca expor credenciais.
4. Respeitar a arquitetura existente.
5. Tratar erros e indisponibilidades.
6. Validar dados enviados e recebidos.
7. Não utilizar dados de produção sem autorização.
8. Não afirmar que uma integração funciona sem evidências de validação.
9. Documentar limitações e dependências externas.