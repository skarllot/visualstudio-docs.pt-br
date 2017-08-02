---
title: "XML Schema Explorer | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XML Schema Explorer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O XML Schema Explorer está integrado com o Microsoft Visual Studio e o Editor de XML para permitir que você trabalhe com esquemas da linguagem XSD.  Quando você abre um arquivo de esquema XML, o nó **Conjunto de Esquemas** aparece no XML Schema Explorer.  Todos os esquemas incluídos, importados ou redefinidos para o arquivo de destino, assim como os arquivos que são referenciados por meio de uma instrução `include` ou `import`, também aparecem no XML Schema Explorer.  
  
 O XML Schema Explorer permite que você faça o seguinte:  
  
-   Obter uma visão geral rápido do conjunto de esquema.  
  
-   Procurar e navegar na árvore.  
  
-   Realizar pesquisas de palavra\-chave e específicas do esquema.  Para obter mais informações, consulte [Procurando o conjunto de esquema](../xml-tools/searching-the-schema-set.md).  
  
-   Adicionar os resultados de pesquisa à Exibição de Gráfico ou Exibição de Modelo de Conteúdo  
  
-   Classificar a árvore pela ordem de documento, tipo ou nome.  Para obter mais informações, consulte [Classificação, filtragem e agrupamento](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).  
  
-   Abra o Editor de XML e pule para as localizações de código no arquivo XSD.  Para obter mais informações, consulte [Integration with XML Editor](../xml-tools/integration-with-xml-editor.md).  
  
-   Gere o exemplo de XML para elementos globais.  
  
 O XML Schema Explorer fornece uma exibição hierárquica do conjunto de esquema por meio de uma exibição de árvore.  O XML Schema Explorer também fornece pesquisa, filtragem, navegação e classificação.  Para acessar o XML Schema Explorer, faça o seguinte:  
  
-   Se você estiver na [Exibição Inicial](../xml-tools/start-view.md), clique no link do **XML Schema Explorer**.  
  
-   Se você estiver na [Exibição de Gráfico](../xml-tools/graph-view.md) ou na [Exibição de Modelo de Conteúdo](../xml-tools/content-model-view.md) e tiver nós em seu espaço de trabalho, use o menu de contexto para selecionar o XML Schema Explorer.  
  
-   Você também pode selecionar o XML Schema Explorerdo menu **Exibição**.  
  
-   Você pode acessar o XML Schema Explorerdo arquivo .vb que tem um literal XML do Visual Basic associado a um arquivo .xsd.  Para ver o esquema definido no XML Schema Explorer, clique com o botão direito do mouse em um nó XML em um literal XML ou uma importação de namespace XML e selecione o comando **Mostrar no Schema Explorer**.  Para obter mais informações, consulte [Integration of XML Literals with XML Schema Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).  
  
## Exibição de árvore  
 O XML Schema Explorer exibe informações de conjunto de esquema pré\-compilado em uma estrutura de árvore.  A estrutura de árvore é organizada da seguinte maneira:  
  
-   No nível superior está o nó do conjunto de esquema.  
  
-   O segundo nível contém os namespaces.  
  
-   O terceiro nível contém os arquivos.  
  
-   O quarto nível contém os nós globais.  Isso pode incluir elementos, grupos, tipos complexos, tipos simples, atributos, grupos de atributo e instruções `include`, `import` e `redefine`.  
  
 A seguir veja um exemplo de uma estrutura de árvore:  
  
 ![XML Schema Explorer](~/xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")  
  
## Seleção e ativação  
 Para realçar e selecionar um nó, clique uma vez no Schema Explorer.  
  
 Para ativar um nó, clique duas vezes ou pressione **Enter** quando o nó estiver selecionado.  
  
-   Ativar um nó abre o arquivo no qual o nó está definido \(se o arquivo já não estiver aberto\) e seleciona o nó no arquivo.  
  
-   Ativar um nó de arquivo abre o arquivo selecionado \(se ele já não estiver aberto\) e destaca o nó `<schema>`.  
  
-   Ativar um SchemaSet ou um nó de namespace não fará nada.  
  
## Nós de arrastar e soltar  
 Você pode arrastar e soltar nós globais, nós de arquivo e nós de namespace em uma exibição do Designer XSD.  Se a exibição atual for a [Exibição Inicial](../xml-tools/start-view.md), arrastar um nó para a exibição abrirá a [Exibição Gráfica](../xml-tools/graph-view.md).  Se a exibição atual for a [Exibição de Modelo de Conteúdo](../xml-tools/content-model-view.md) ou Exibição Gráfica, a exibição não será alterada quando você soltar um nó nela.  
  
 Soltar arquivos na exibição adicionará todos os nós globais no arquivo para o [Espaço de Trabalho do Designer XSD](../xml-tools/xml-schema-designer-workspace.md).  Soltar namespaces na exibição adicionará todos os nós globais no namespace para o espaço de trabalho.  O espaço de trabalho é compartilhado entre todas as visualizações.  
  
 Você não pode arrastar e soltar nós locais ou importações.  
  
## Nesta seção  
  
-   [Searching the Schema Set](../xml-tools/searching-the-schema-set.md)  
  
-   [Sorting, Filtering, and Grouping](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)  
  
-   [Context Menus](../xml-tools/context-menus-xml-schema-explorer.md)  
  
-   [Integration of XML Literals with XML Schema Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)  
  
## Consulte também  
 [How to: Add Nodes to the Workspace from the XML Schema Explorer](../Topic/How%20to:%20Add%20Nodes%20to%20the%20Workspace%20from%20the%20XML%20Schema%20Explorer.md)