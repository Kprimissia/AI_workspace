---
name: frontend-development
description: Desenvolve, analisa, corrige, refatora e valida aplicações front-end. Utilize esta skill para trabalhar com interfaces web, componentes, páginas, navegação, responsividade, acessibilidade, integração com APIs e qualidade de código.
---

# Front-end Development

## 1. Objetivo

Estabelecer um procedimento técnico reutilizável para desenvolver e manter aplicações front-end com qualidade, organização, segurança e facilidade de manutenção.

Esta Skill orienta o agente durante todo o ciclo de desenvolvimento, desde a análise inicial até a validação da implementação.

## 2. Escopo

Esta Skill pode ser utilizada em projetos que envolvam:

- HTML e CSS.
- JavaScript e TypeScript.
- React e outros frameworks front-end.
- Componentização.
- Gerenciamento de estado.
- Roteamento.
- Consumo de APIs.
- Interfaces responsivas.
- Acessibilidade.
- Testes de interface.
- Otimização de desempenho.

A tecnologia efetivamente utilizada deve ser identificada no projeto. Não introduzir frameworks ou bibliotecas apenas porque aparecem nesta lista.

## 3. Pré-requisitos

Antes de iniciar:

1. Identificar o projeto e seu diretório raiz.
2. Consultar as instruções do projeto, incluindo `AGENTS.md`.
3. Identificar as tecnologias e versões utilizadas.
4. Analisar a estrutura de diretórios.
5. Consultar `package.json` e arquivos de configuração, quando existentes.
6. Identificar padrões de componentes, estilos e organização.
7. Verificar o estado do Git.
8. Compreender o requisito solicitado.

Não começar implementações sem compreender a arquitetura existente.

## 4. Fluxo de desenvolvimento

### Etapa 1 — Análise do requisito

Identificar:

- Objetivo da funcionalidade.
- Usuário que utilizará a interface.
- Comportamento esperado.
- Componentes envolvidos.
- Dados necessários.
- Integrações existentes.
- Critérios de aceite.

Quando houver informações insuficientes, identificar as lacunas antes de tomar decisões importantes.

### Etapa 2 — Análise da arquitetura

Investigar:

- Organização das pastas.
- Componentes existentes.
- Páginas e rotas.
- Contextos e estados globais.
- Hooks.
- Serviços e camada de API.
- Estilos globais e locais.
- Bibliotecas utilizadas.
- Padrões de nomenclatura.

Priorizar a reutilização das estruturas existentes.

### Etapa 3 — Planejamento

Definir:

- Arquivos que precisam ser criados.
- Arquivos que precisam ser modificados.
- Componentes reutilizáveis.
- Dependências necessárias.
- Estratégia de implementação.
- Possíveis impactos em outras funcionalidades.
- Formas de validação.

Para tarefas simples, realizar o planejamento internamente e executar diretamente. Para tarefas complexas, apresentar o plano ao usuário.

### Etapa 4 — Implementação

Durante o desenvolvimento:

- Respeitar a arquitetura existente.
- Criar componentes com responsabilidades bem definidas.
- Evitar componentes excessivamente grandes.
- Utilizar nomes claros.
- Evitar duplicação de código.
- Manter tipagem adequada quando utilizar TypeScript.
- Separar apresentação, lógica e acesso a dados quando apropriado.
- Tratar erros e estados inesperados.
- Preservar funcionalidades existentes.
- Evitar alterações não relacionadas ao requisito.

### Etapa 5 — Interface e experiência do usuário

Considerar:

**Responsividade**
- Desktop.
- Tablets.
- Dispositivos móveis.
- Diferentes resoluções e orientações.

**Usabilidade**
- Navegação intuitiva.
- Hierarquia visual.
- Consistência entre telas.
- Feedback das ações.
- Formulários compreensíveis.

**Estados da interface**
- Carregamento.
- Sucesso.
- Erro.
- Estado vazio.
- Dados indisponíveis.
- Ações desabilitadas.

**Acessibilidade**
- HTML semântico.
- Labels apropriados.
- Navegação por teclado.
- Contraste adequado.
- Textos alternativos para imagens.
- Identificação clara de erros.

### Etapa 6 — Integração com APIs

Quando a funcionalidade depender de um serviço externo ou back-end:

1. Identificar a camada de comunicação existente.
2. Consultar os contratos reais da API.
3. Conferir métodos HTTP e parâmetros.
4. Verificar os formatos de requisição e resposta.
5. Implementar tratamento de erros.
6. Considerar estados de carregamento.
7. Evitar chamadas duplicadas ou desnecessárias.
8. Validar o comportamento da integração.

Nunca inventar endpoints ou presumir que uma integração funciona sem evidências.

Respeitar as permissões de atuação definidas pelo projeto. Esta Skill não autoriza alterações no back-end.

### Etapa 7 — Testes e validação

Executar as verificações pertinentes ao projeto:

- Lint.
- Testes automatizados.
- Build.
- Verificação de tipos.
- Testes de navegação.
- Validação de formulários.
- Verificação de responsividade.
- Inspeção de erros no console, quando possível.

Corrigir problemas encontrados dentro do escopo autorizado.

Não declarar uma validação como concluída quando ela não tiver sido executada.

### Etapa 8 — Revisão final

Antes de finalizar:

- Verificar arquivos modificados.
- Procurar código duplicado.
- Identificar imports não utilizados.
- Verificar erros de tipagem.
- Conferir consistência visual.
- Avaliar possíveis regressões.
- Confirmar que o requisito foi atendido.
- Verificar se a documentação precisa ser atualizada.

## 5. Padrões de qualidade

Toda implementação deve priorizar:

- Legibilidade.
- Manutenibilidade.
- Reutilização.
- Segurança.
- Acessibilidade.
- Responsividade.
- Desempenho adequado.
- Consistência arquitetural.
- Simplicidade.

Evitar abstrações desnecessárias e soluções complexas para problemas simples.

## 6. Gerenciamento de dependências

Antes de instalar uma biblioteca:

1. Verificar se o projeto já possui uma solução equivalente.
2. Avaliar se a dependência é realmente necessária.
3. Considerar tamanho, manutenção e compatibilidade.
4. Explicar a necessidade quando a instalação representar uma mudança relevante.

Não atualizar dependências indiscriminadamente.

## 7. Proteção do trabalho da equipe

Em projetos colaborativos:

- Verificar alterações locais antes de modificar arquivos.
- Preservar trabalho não commitado.
- Não sobrescrever implementações de outros integrantes.
- Respeitar branches e convenções.
- Não realizar commit ou push sem autorização.

## 8. Resultado esperado

Ao concluir uma tarefa, apresentar:

### Resumo
O que foi desenvolvido ou corrigido.

### Arquivos
Quais arquivos foram criados ou modificados.

### Decisões técnicas
Principais escolhas realizadas e suas justificativas.

### Validação
Testes e verificações executados, com seus resultados.

### Pendências
Problemas não resolvidos, dependências externas ou validações não realizadas.

## 9. Diretriz final

Desenvolver soluções front-end que atendam aos requisitos reais do projeto, respeitem sua arquitetura e possam ser mantidas pela equipe.

A qualidade da implementação deve ser avaliada não apenas pela aparência ou pelo funcionamento imediato, mas também pela organização, acessibilidade, segurança e sustentabilidade do código.