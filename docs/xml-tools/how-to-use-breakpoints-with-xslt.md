---
title: "How to: Use Breakpoints with XSLT | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Use Breakpoints with XSLT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode definir pontos de interrupção em uma folha de estilos XSLT ou no documento de código\-fonte XML.  Se você definir um ponto de interrupção em uma marca, quando a execução iniciar o ponto de interrupção se transportará para a instrução que tem a seguinte linha de código informações.  
  
 Para obter mais informações, consulte [Debugging Basics: Breakpoints](http://msdn.microsoft.com/pt-br/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).  
  
## Definir um ponto de interrupção em uma folha de estilos  
 Os pontos de interrupção podem ser definidos em marcas inicial, em marcas de fim, e em nós de texto de uma folha de estilos XSLT.  Os pontos de interrupção também podem ser definidos no código em um bloco de script.  
  
#### Para definir um ponto de interrupção em uma folha de estilos  
  
1.  Abra uma folha de estilos no editor XML.  
  
2.  Posicione o cursor no local de ponto de interrupção, clique com o botão direito do mouse, aponte para **Ponto de Interrupção**, e clique **Inserir Ponto de Interrupção**.  
  
3.  Clique em procurar o botão procurar \(**...**\) no campo **Entrada** da janela de propriedades do documento.  
  
4.  Localize o documento\-fonte XML e clique **Abrir**.  
  
     Isso define o arquivo de documento de origem que é usado para a transformação XSLT.  
  
5.  Clique no botão de **Depurar XSL** na barra de ferramentas do editor XML.  
  
## Definir um ponto de interrupção em um documento\-fonte XML  
 Os pontos de interrupção podem ser definidas em elementos, atributos, no nó de namespace, nos comentários, na instrução de processamento, e os nós de texto de um documento\-fonte XML.  Você não pode definir um ponto de interrupção no nó do documento, ou em um nó de namespace que é herdada de elemento pai.  
  
#### Para definir um ponto de interrupção em um documento\-fonte XML  
  
1.  Abra o documento XML no editor XML.  
  
2.  Posicione o cursor no local de ponto de interrupção, clique com o botão direito do mouse, aponte para **Ponto de Interrupção**, e clique **Inserir Ponto de Interrupção**.  
  
3.  Clique no botão procurar \(**...**\) no campo **Folha de Estilos** da janela de propriedades do documento.  
  
4.  Localize o documento\-fonte XML e clique **Abrir**.  
  
     Isso define o arquivo de documento de origem que é usado para a transformação XSLT.  
  
5.  Clique no botão de **Depurar XSL** na barra de ferramentas do editor XML.  
  
## Consulte também  
 [Walkthrough: Debug an XSLT Style Sheet](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)