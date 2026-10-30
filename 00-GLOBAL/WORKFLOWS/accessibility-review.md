# Workflow — Acessibilidade e Experiência do Usuário (UX/UI)

## Objetivo

Orientar o agente na análise, implementação e melhoria da experiência do usuário e da acessibilidade em aplicações, garantindo interfaces intuitivas, consistentes, responsivas e utilizáveis por diferentes pessoas e dispositivos.

## 1. Compreender o contexto

Antes de realizar alterações:

- Identificar o objetivo da interface.
- Compreender o público-alvo.
- Identificar os principais fluxos de utilização.
- Verificar os dispositivos utilizados.
- Consultar a identidade visual do projeto.
- Identificar padrões de navegação existentes.
- Verificar requisitos de acessibilidade.

Não modificar a identidade visual ou a experiência existente sem compreender as necessidades do projeto.

## 2. Analisar a experiência do usuário

Avaliar:

- Facilidade de navegação.
- Clareza das informações.
- Organização do conteúdo.
- Hierarquia visual.
- Consistência entre telas.
- Facilidade de encontrar funcionalidades.
- Clareza das ações disponíveis.
- Feedback após interações.
- Prevenção e recuperação de erros.
- Quantidade de etapas necessárias para concluir tarefas.

Identificar pontos de confusão e dificuldades nos fluxos de utilização.

## 3. Avaliar a interface visual

Verificar:

- Alinhamento.
- Espaçamento.
- Tipografia.
- Contraste.
- Cores.
- Hierarquia dos elementos.
- Consistência dos componentes.
- Legibilidade.
- Organização das informações.
- Estados visuais dos elementos interativos.

Respeitar o design system e os padrões visuais existentes.

## 4. Verificar responsividade

Avaliar a interface em diferentes tamanhos de tela:

- Celulares.
- Tablets.
- Notebooks.
- Monitores desktop.

Verificar:

- Adaptação dos layouts.
- Comportamento de menus.
- Redimensionamento de componentes.
- Legibilidade dos textos.
- Espaçamento entre elementos.
- Rolagem horizontal desnecessária.
- Funcionamento de formulários.
- Acessibilidade dos controles em telas sensíveis ao toque.

Não considerar uma interface responsiva apenas porque ela utiliza CSS flexível ou grid.

## 5. Avaliar acessibilidade

Utilizar como referência as diretrizes WCAG, considerando o nível de conformidade adequado ao projeto.

Verificar:

- Estrutura semântica do HTML.
- Hierarquia correta de títulos.
- Textos alternativos para imagens relevantes.
- Identificação dos campos de formulário.
- Contraste adequado entre texto e fundo.
- Navegação por teclado.
- Indicadores visíveis de foco.
- Uso adequado de atributos ARIA.
- Identificação de erros.
- Mensagens compreensíveis.
- Compatibilidade com tecnologias assistivas.

Não utilizar ARIA quando elementos HTML nativos já oferecem a semântica necessária.

## 6. Avaliar formulários e interações

Verificar:

- Identificação clara dos campos.
- Indicação de campos obrigatórios.
- Mensagens de validação compreensíveis.
- Feedback de sucesso e erro.
- Prevenção de envios duplicados.
- Estados de carregamento.
- Confirmação de ações importantes.
- Navegação por teclado.
- Facilidade de utilização em dispositivos móveis.

Os erros devem indicar o problema e orientar o usuário sobre como corrigi-lo.

## 7. Avaliar estados da interface

Considerar os principais estados:

- Carregamento.
- Sucesso.
- Erro.
- Ausência de dados.
- Lista vazia.
- Ação desabilitada.
- Falta de conexão.
- Acesso não autorizado.

Evitar interfaces que deixem o usuário sem informação sobre o resultado de uma ação.

## 8. Planejar melhorias

Antes de implementar:

1. Registrar os problemas identificados.
2. Identificar as telas e componentes afetados.
3. Classificar a gravidade.
4. Priorizar problemas que impedem ou dificultam a utilização.
5. Definir as melhorias propostas.
6. Avaliar impactos na identidade visual e na arquitetura.

Não realizar alterações visuais extensas sem necessidade.

## 9. Implementar melhorias

Durante a implementação:

- Reutilizar componentes existentes.
- Preservar a identidade visual.
- Manter consistência entre páginas.
- Utilizar HTML semântico.
- Garantir navegação por teclado.
- Implementar estados de interação.
- Evitar elementos visuais desnecessários.
- Manter layouts responsivos.
- Não prejudicar funcionalidades existentes.

## 10. Validar a interface

Executar, quando aplicável:

- Testes em diferentes resoluções.
- Navegação utilizando somente teclado.
- Verificação de contraste.
- Testes de formulários.
- Verificação de hierarquia semântica.
- Testes com ferramentas de acessibilidade.
- Testes com leitores de tela, quando disponíveis.
- Testes dos principais fluxos de utilização.

Ferramentas automatizadas ajudam na análise, mas não substituem avaliações manuais.

## 11. Documentar

Registrar:

- Telas avaliadas.
- Problemas identificados.
- Critérios de acessibilidade utilizados.
- Melhorias implementadas.
- Componentes modificados.
- Testes realizados.
- Problemas ainda existentes.

## 12. Git e colaboração

- Respeitar os padrões visuais definidos pela equipe.
- Preservar alterações de outros integrantes.
- Evitar modificar componentes compartilhados sem avaliar impactos.
- Comunicar mudanças que afetem outras telas.
- Não executar operações destrutivas sem autorização.
- Não realizar commit, push ou merge sem autorização explícita.

## 13. Relatório final

Apresentar:

- Telas e fluxos analisados.
- Problemas encontrados.
- Classificação dos problemas.
- Melhorias realizadas.
- Arquivos modificados.
- Testes executados.
- Resultado das validações.
- Limitações identificadas.
- Recomendações futuras.

## Regras obrigatórias

1. Priorizar a facilidade de utilização.
2. Respeitar a identidade visual do projeto.
3. Considerar diferentes dispositivos e resoluções.
4. Seguir boas práticas de acessibilidade.
5. Não depender exclusivamente de cores para transmitir informações.
6. Garantir alternativas para interações que dependam de mouse.
7. Não considerar testes automatizados como garantia de acessibilidade completa.
8. Preservar funcionalidades existentes.
9. Não afirmar conformidade com WCAG sem avaliação adequada.
10. Priorizar problemas que impeçam o acesso ou a conclusão de tarefas.