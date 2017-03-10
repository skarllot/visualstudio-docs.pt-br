---
title: "How to: Evaluate an XPath Expression | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Evaluate an XPath Expression
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode avaliar expressões XPath com a caixa de diálogo **QuickWatch** .  A expressão XPath deve ser válido de acordo com a recomendação XPath 1,0 W3C.  XSLT de contexto atual, que é o nó de `self::node()` em **Locais** de fornece o contexto de avaliação da expressão XPath.  
  
 A lista a seguir descreve quais funções são suportadas para avaliar uma expressão XPath:  
  
-   As funções internas XPath são suportadas.  
  
-   As funções internas XSLT não são suportadas.  
  
-   As funções definidas pelo usuário não são suportadas.  
  
> [!NOTE]
>  O procedimento a seguir usa arquivos de belowAvg.xsl e de books.xml do tópico de [Walkthrough: Debug an XSLT Style Sheet](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) .  
  
### Para avaliar uma expressão XPath  
  
1.  Inserir um ponto de interrupção na tag de início de `xsl:if` .  
  
2.  Clique no botão de **Depurar XSL** na barra de ferramentas do editor XML.  
  
     Inicia e as quebras do depurador na marca `xsl:if` .  
  
3.  Clique com o botão direito do mouse e selecione **QuickWatch**.  
  
     A caixa de diálogo **QuickWatch** é exibida.  
  
4.  Entre em `./price/text()` no campo de **Expressão** da caixa de diálogo **QuickWatch** e clique **Reavaliar**.  
  
     O custo do nó atual do catálogo aparece na caixa de **Valor** .  
  
5.  Altere a expressão XPath a `./price/text() < $bookAverage` e clique **Reavaliar**.  
  
     A caixa de **Valor** mostra que avalia a expressão XPath a `true`.  
  
## Consulte também  
 [Debugging XSLT](../xml-tools/debugging-xslt.md)