---
title: "Searching the Schema Set | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Searching the Schema Set
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML Schema Explorer permite que você procurar o esquema define as seguintes maneiras:  
  
-   Pesquisa de palavras\-chave.  
  
-   Pesquisa Esquema\- específica.  
  
## Palavra\-chave pesquisa  
 Você executar pesquisas de palavras\-chave inserindo uma subcadeia de caracteres na caixa de texto **Pesquisa SchemaSet** da barra de ferramentas XML Schema Explorer.  
  
 ![XML Schema Explorer Keyword Search](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 XML Schema Explorer procura o esquema definido pelo seguinte:  
  
-   Alguns atributos de `name` ou de `ref` que corresponderem a palavra\-chave especificada.  Isso permite que você encontrar elementos, atributos, tipos, e assim por diante por nome.  
  
-   Atributos de `schemaLocation` de incluem instruções.  
  
-   Atributos de `namespace` de instruções de importação.  
  
## Pesquisar esquema específico  
 XML Schema Explorer também inclui as pesquisas internos que você pode acessar usando o menu de contexto XML Schema Explorer.  Para obter mais informações sobre menus de contexto disponíveis, consulte [Context Menus](../xml-tools/context-menus-xml-schema-explorer.md).  Você também pode executar uma visualização esquema\- específica de pesquisa do início; para obter mais informações, consulte a seção “esquema para detalhes para” no tópico de [Start View](../xml-tools/start-view.md) .  
  
## Exibindo e navegando resultados de pesquisa  
 Depois que a pesquisa é concluída, o painel de resultados de resumo é adicionado à barra de ferramentas com os resultados da pesquisa.  Os resultados de pesquisa também são realçadas em XML Schema Explorer e marcados por escalas na barra de rolagem vertical.  Você pode navegar nos resultados de pesquisa usando botões de **Ir para o Próximo Resultado da Pesquisa** e de **Ir para o Resultado da Pesquisa Anterior** no painel de resultados de resumo da barra de ferramentas XML Schema Explorer; usando as teclas de teclado e Shift\+F3; F3 ou clicando nas marcas de escala na barra de rolagem.  
  
 Você pode adicionar os resultados de pesquisa para o espaço de trabalho clicando no botão de **Adicionar nós realçados ao Espaço de Trabalho** no painel de resultados de resumo.  
  
 ![XML Schema Explorer Search Result](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## Resultados da pesquisa de esclarecimento  
 Para limpar os resultados de pesquisa, clique no botão de **x** no painel de resultados de resumo da barra de ferramentas XML Schema de Pesquisa.  
  
## Consulte também  
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)