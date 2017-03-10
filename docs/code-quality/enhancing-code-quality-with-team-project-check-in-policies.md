---
title: "Melhorando a qualidade do c&#243;digo com pol&#237;ticas de check-in do projeto da equipe | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "qualidade do código, usando diretivas de check-in"
  - "desenvolvimento em equipe, melhorando a qualidade do código"
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Melhorando a qualidade do c&#243;digo com pol&#237;ticas de check-in do projeto da equipe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando você usa o controle de versão do Team Foundation \(TFVC\), você pode criar diretivas de check\-in para os projetos de equipe. para impor práticas que levam a códigos melhores e mais eficiente do desenvolvimento de grupo. Diretivas de check\-in são regras que são definidas no nível do projeto de equipe e aplicadas em computadores de desenvolvedor antes que o código tem permissão para fazer check\-in.  
  
 Você pode especificar essas diretivas de check\-in do projeto equipe:  
  
-   **Cria**: requer que as interrupções na compilação que foram criadas durante uma compilação devem ser corrigidas antes de um novo check\-in.  
  
-   **Comentários Changeset**: requer que os usuários forneçam comentários ao fazer check\-in das alterações.  
  
-   **a análise de código**: exige que a análise de código é executada antes do check\-in.  
  
-   **Itens de trabalho**: requer que um ou mais itens de trabalho seja associado a seleção\-no.  
  
> [!IMPORTANT]
>  Para usar políticas de check\-in, você deve estar conectado para [!INCLUDE[vststfsLong](../code-quality/includes/vststfslong_md.md)].  
  
## Tarefas comuns  
  
|Tarefa|Conteúdo de suporte|  
|------------|-------------------------|  
|**Criação e uso de políticas check\-in:** criar diretivas de check\-in usando as configurações do projeto de equipe de [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)].|[Definir e impor restrições de qualidade](../Topic/Set%20and%20Enforce%20Quality%20Gates.md)|  
|**Criar e usar código análise políticas check\-in:** você pode escolher entre um conjunto padrão de regras de análise de código, ou você pode criar um conjunto personalizado.|[Criando e usando políticas de check\-in de análise do código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|  
  
## Tarefas relacionadas  
  
|Tarefa|Conteúdo de suporte|  
|------------|-------------------------|  
|**Configurar seu ambiente de desenvolvimento:** antes de criar ou modificar o código, você deve configurar seus ambientes de desenvolvimento e teste usando o código\-fonte apropriada. Se você estiver trabalhando com bancos de dados, você também deve ter acesso à sua representação offline.|[Configurar ambientes de desenvolvimento](http://msdn.microsoft.com/pt-br/7b686610-d379-4ca0-9608-73ef0e576e3a)|  
|**Uso de análise de código no processo de desenvolvimento:** os membros da equipe executam análise de código em seus computadores de desenvolvimento. No Visual Studio, os desenvolvedores configurar e executar análise de código seja executado para projetos de código individuais, exibir em analisar problemas encontrados pelas execuções e criar itens de trabalho para avisos.|[Analisando a qualidade do aplicativo](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|  
|**Criação e testes de unidade de execução:** testes de unidade dão aos desenvolvedores e testadores uma maneira rápida para procurar erros lógicos nos métodos de classes em projetos c\#, Visual Basic .NET e C\+\+. Um teste de unidade pode ser criado uma vez e executar toda vez que o código fonte é alterado para certificar\-se de que não há bugs são introduzidas.|[Teste de unidade de código](../test/unit-test-your-code.md)|  
|**Acompanhar itens de trabalho e defeitos:** você pode usar os itens de trabalho para acompanhar e gerenciar seu trabalho e informações sobre seu projeto de equipe. Um item de trabalho é um banco de dados de registro [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] usa para controlar a atribuição e o andamento do trabalho. Você pode usar tipos diferentes de itens de trabalho para acompanhar os diferentes tipos de trabalho, como tarefas de desenvolvimento, bugs do produto e requisitos do cliente.|[Acompanhe o trabalho e gerenciar o fluxo de trabalho &#91;redirecionado&#93;](http://msdn.microsoft.com/pt-br/d2d8637d-0ef8-4ca3-874e-a04713344032)|  
  
## Recursos externos  
  
### Diretrizes  
 [Teste para entrega contínua com o Visual Studio 2012 – capítulo 2: testes de unidade: Testando o interior](http://go.microsoft.com/fwlink/?LinkID=255188)