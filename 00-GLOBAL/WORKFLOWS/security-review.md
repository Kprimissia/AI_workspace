# Workflow — Segurança e Análise de Vulnerabilidades

## Objetivo

Orientar o agente na identificação, análise, prevenção e correção de vulnerabilidades em aplicações e sistemas, priorizando a proteção de dados, a integridade das operações e o controle de acesso.

## 1. Entender o contexto

Antes de iniciar a análise:

- Identificar o projeto e sua finalidade.
- Compreender a arquitetura.
- Identificar os módulos envolvidos.
- Verificar tecnologias e dependências.
- Identificar dados sensíveis tratados pelo sistema.
- Entender os perfis de usuários e suas permissões.
- Consultar políticas e requisitos de segurança existentes.

Não presumir que uma aplicação é segura apenas porque possui autenticação.

## 2. Inspecionar a superfície de ataque

Analisar, conforme aplicável:

- Autenticação.
- Autorização.
- Gerenciamento de sessões.
- APIs e endpoints.
- Formulários e entradas de usuários.
- Banco de dados.
- Upload e download de arquivos.
- Integrações externas.
- Dependências.
- Configurações de ambiente.
- Logs e mensagens de erro.
- Infraestrutura e publicação.

Identificar pontos de entrada e componentes que possam expor o sistema.

## 3. Verificar vulnerabilidades comuns

Investigar possíveis ocorrências de:

- SQL Injection.
- Cross-Site Scripting (XSS).
- Cross-Site Request Forgery (CSRF).
- Broken Access Control.
- Falhas de autenticação.
- Exposição de informações sensíveis.
- Insecure Direct Object Reference (IDOR).
- Configurações inseguras.
- Dependências vulneráveis.
- Upload inseguro de arquivos.
- Validação inadequada de entradas.
- Gerenciamento inadequado de sessões.
- Falhas de controle de permissões.

Utilizar referências reconhecidas, como OWASP Top 10 e OWASP ASVS, quando pertinentes.

## 4. Avaliar autenticação e autorização

Verificar:

- Se as credenciais são tratadas com segurança.
- Se as senhas são armazenadas utilizando mecanismos apropriados de hash.
- Se tokens são protegidos.
- Se sessões possuem controles adequados.
- Se as permissões são verificadas no servidor.
- Se usuários conseguem acessar somente recursos autorizados.
- Se existem proteções contra tentativas excessivas de autenticação.
- Se operações administrativas possuem controles adicionais quando necessários.

A interface não deve ser considerada uma barreira de segurança suficiente.

## 5. Avaliar proteção de dados

Verificar:

- Quais dados pessoais são armazenados.
- Se existe necessidade real de cada dado coletado.
- Se informações sensíveis são protegidas.
- Se dados são transmitidos por canais seguros.
- Se logs evitam exposição de informações privadas.
- Se backups possuem proteção adequada.
- Se existem políticas de retenção e descarte.
- Se o tratamento respeita os requisitos aplicáveis da LGPD.

Nunca reproduzir credenciais ou dados pessoais reais em relatórios desnecessários.

## 6. Analisar dependências e configurações

Inspecionar:

- Bibliotecas e versões.
- Dependências desatualizadas.
- Vulnerabilidades conhecidas.
- Arquivos de configuração.
- Variáveis de ambiente.
- Permissões excessivas.
- Serviços expostos.
- Configurações de desenvolvimento e produção.

Não atualizar dependências automaticamente sem avaliar compatibilidade e impacto.

## 7. Classificar os riscos

Classificar os problemas encontrados:

- **CRÍTICO:** possibilidade de comprometimento grave do sistema ou exposição significativa de dados.
- **ALTO:** vulnerabilidade com impacto relevante e possibilidade concreta de exploração.
- **MÉDIO:** risco limitado ou dependente de determinadas condições.
- **BAIXO:** impacto reduzido.
- **INFORMATIVO:** recomendação de melhoria ou observação sem vulnerabilidade confirmada.

Para cada achado, registrar:

- Identificador.
- Severidade.
- Arquivo, módulo ou componente afetado.
- Descrição.
- Evidência.
- Impacto.
- Condições de exploração, quando conhecidas.
- Recomendação de correção.

Não classificar uma suspeita como vulnerabilidade confirmada sem evidências suficientes.

## 8. Planejar correções

Antes de corrigir:

1. Identificar a causa.
2. Avaliar o impacto.
3. Identificar componentes relacionados.
4. Definir a solução adequada.
5. Verificar riscos de regressão.
6. Planejar os testes.

Priorizar vulnerabilidades críticas e altas.

## 9. Implementar correções

Durante a correção:

- Aplicar validação adequada de entradas.
- Implementar controles de autorização.
- Proteger credenciais e tokens.
- Utilizar consultas parametrizadas.
- Aplicar codificação de saída adequada ao contexto.
- Restringir permissões.
- Proteger operações sensíveis.
- Atualizar dependências quando necessário.
- Preservar funcionalidades legítimas.
- Seguir os padrões de segurança do projeto.

Não implementar mecanismos de segurança improvisados quando existem soluções consolidadas.

## 10. Validar a segurança

Após as correções:

- Reexecutar os testes relacionados.
- Verificar se a vulnerabilidade foi eliminada.
- Testar cenários de acesso autorizado e não autorizado.
- Verificar possíveis regressões.
- Executar ferramentas de análise disponíveis.
- Revisar as alterações.
- Registrar riscos que permanecem.

Testes de segurança devem ocorrer somente em ambientes e sistemas para os quais exista autorização.

## 11. Documentar os resultados

Registrar:

- Escopo da análise.
- Componentes avaliados.
- Vulnerabilidades encontradas.
- Classificação dos riscos.
- Correções realizadas.
- Testes executados.
- Riscos residuais.
- Recomendações futuras.

Não incluir informações que facilitem a exploração de sistemas em relatórios destinados a pessoas não autorizadas.

## 12. Git e colaboração

- Preservar alterações de outros desenvolvedores.
- Não expor segredos em commits.
- Não sobrescrever correções existentes.
- Não executar comandos destrutivos sem autorização.
- Não realizar commit, push, merge ou publicação sem autorização explícita.
- Comunicar vulnerabilidades relevantes aos responsáveis pelo projeto.

## 13. Relatório final

Apresentar:

- Escopo analisado.
- Vulnerabilidades identificadas.
- Severidade de cada achado.
- Evidências.
- Impactos.
- Correções realizadas.
- Testes executados.
- Riscos residuais.
- Recomendações.

## Regras obrigatórias

1. Priorizar a proteção de dados e usuários.
2. Não expor credenciais ou informações sensíveis.
3. Não executar testes ofensivos sem autorização.
4. Não modificar ambientes de produção sem autorização.
5. Não considerar autenticação como substituta de autorização.
6. Não afirmar que um sistema está totalmente seguro.
7. Diferenciar vulnerabilidades confirmadas de suspeitas.
8. Priorizar correções conforme a gravidade.
9. Registrar limitações da análise.
10. Seguir boas práticas reconhecidas de segurança.