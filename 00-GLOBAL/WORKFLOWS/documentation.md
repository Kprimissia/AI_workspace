# Workflow — Documentação de Projetos

## Objetivo

Orientar o agente na criação, atualização e revisão da documentação de projetos de software, garantindo clareza, precisão, organização e facilidade de manutenção.

## 1. Entender a necessidade

Antes de documentar:

- Identificar o objetivo da documentação.
- Entender quem utilizará o documento.
- Identificar o projeto, módulo ou funcionalidade envolvida.
- Verificar se já existe documentação relacionada.
- Identificar o nível de detalhamento necessário.

Não criar documentação sem compreender o funcionamento real do projeto.

## 2. Analisar as fontes

Consultar, quando aplicável:

- Estrutura do repositório.
- Código-fonte.
- Arquivos de configuração.
- Variáveis de ambiente.
- Contratos de API.
- Testes.
- Documentação existente.
- Decisões arquiteturais.
- Requisitos e critérios de aceitação.

O código e as configurações atuais devem ser considerados antes de descrever o funcionamento do sistema.

Não inventar funcionalidades, tecnologias, endpoints ou configurações.

## 3. Planejar o documento

Definir:

- Título.
- Objetivo.
- Público-alvo.
- Estrutura de seções.
- Fontes utilizadas.
- Informações que precisam ser confirmadas.
- Relação com documentos existentes.

Evitar duplicar informações já documentadas.

## 4. Criar ou atualizar a documentação

Selecionar o formato adequado:

- README: apresentação e orientação inicial do projeto.
- Guia de instalação: preparação do ambiente.
- Guia de execução: comandos e procedimentos.
- Documentação de arquitetura: estrutura e responsabilidades.
- Referência de API: endpoints, parâmetros, respostas e autenticação.
- Especificação funcional: requisitos e comportamentos.
- ADR: registro de decisões arquiteturais.
- Guia de usuário: utilização do sistema.
- Relatório técnico: análise, implementação e resultados.

## 5. Garantir precisão técnica

Ao escrever:

- Utilizar informações verificadas.
- Manter nomes de arquivos, pastas, funções e comandos corretos.
- Apresentar exemplos executáveis sempre que possível.
- Identificar claramente informações ainda não confirmadas.
- Não expor senhas, tokens, chaves ou dados pessoais.
- Não registrar credenciais reais em exemplos.
- Diferenciar funcionalidades implementadas de funcionalidades planejadas ou demonstrativas.

## 6. Organizar a escrita

A documentação deve:

- Utilizar títulos e subtítulos objetivos.
- Seguir uma sequência lógica.
- Evitar repetições.
- Explicar termos técnicos quando necessário.
- Utilizar listas e tabelas quando facilitarem a leitura.
- Apresentar comandos em blocos de código.
- Manter consistência de nomenclatura.
- Utilizar linguagem adequada ao público-alvo.

## 7. Revisar o documento

Verificar:

- Correção técnica.
- Clareza e organização.
- Coerência com o código atual.
- Links e referências.
- Comandos e exemplos.
- Informações desatualizadas.
- Duplicações.
- Dados sensíveis.
- Compatibilidade com os padrões do projeto.

## 8. Manutenção

Quando o código ou a arquitetura mudar:

- Identificar documentos afetados.
- Atualizar somente as informações necessárias.
- Preservar informações ainda válidas.
- Remover instruções comprovadamente obsoletas.
- Verificar referências cruzadas.
- Registrar decisões importantes quando aplicável.

## 9. Git e colaboração

- Respeitar a estrutura documental existente.
- Evitar sobrescrever documentos de outros integrantes.
- Preservar alterações não relacionadas.
- Não executar operações destrutivas sem autorização.
- Não realizar commit, push ou merge sem autorização explícita.

## 10. Relatório final

Informar:

- Documento criado ou atualizado.
- Objetivo e conteúdo.
- Arquivos consultados.
- Informações confirmadas.
- Informações pendentes.
- Pontos que precisam de revisão humana.

## Regras obrigatórias

1. Nunca inventar informações técnicas.
2. Não documentar funcionalidades como concluídas sem evidências.
3. Não expor dados sensíveis.
4. Não duplicar documentação sem necessidade.
5. Priorizar clareza, precisão e manutenção.
6. Respeitar os padrões e a estrutura do projeto.
7. Manter a documentação coerente com a implementação real.