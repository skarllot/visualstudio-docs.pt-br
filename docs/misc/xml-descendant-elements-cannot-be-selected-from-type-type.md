---
title: "Elementos descendentes XML n&#227;o podem ser selecionados do tipo &#39;type&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36809"
  - "bc36809"
helpviewer_keywords: 
  - "BC36809"
ms.assetid: 560a3370-f24d-4ca3-93b1-39aabe13c238
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elementos descendentes XML n&#227;o podem ser selecionados do tipo &#39;type&#39;
Um descendente XML foi referenciado por um objeto que não é do tipo <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument>, ou `IEnumerable(Of XElement)`. Para obter mais informações, consulte [Propriedade de eixo descendente XML](/dotnet/visual-basic/language-reference/xml-axis/xml-descendant-axis-property).  
  
```vb#  
' Generates an error. Dim var = "sample text"...<childElement>  
```  
  
 **ID do erro:** BC36809  
  
### Para corrigir este erro  
  
-   Certifique\-se de que o objeto do qual você está fazendo referência a um elemento descendente é altamente tipado como <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument>, ou `IEnumerable(Of XElement)`. A seguir está um exemplo:  
  
    ```vb#  
    Dim elem As XElement = <root> <child /> </root> Dim var = elem...<child>  
    ```  
  
## Consulte também  
 [Propriedade de eixo descendente XML](/dotnet/visual-basic/language-reference/xml-axis/xml-descendant-axis-property)   
 [Propriedades do eixo XML](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)