---
title: "Elementos XML n&#227;o podem ser selecionados do tipo &#39;type&#39; | Microsoft Docs"
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
  - "vbc36807"
  - "bc36807"
helpviewer_keywords: 
  - "BC36807"
ms.assetid: 01c19899-2b44-41e9-a99c-35edfa0deaf1
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elementos XML n&#227;o podem ser selecionados do tipo &#39;type&#39;
Um elemento filho XML foi referenciado para um objeto que não é do tipo <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument>, ou `IEnumerable(Of XElement)`. Para obter mais informações, consulte [Propriedade do eixo filho XML](/dotnet/visual-basic/language-reference/xml-axis/xml-child-axis-property).  
  
```vb#  
' Generates an error. Dim var = "sample text".<child>  
```  
  
 **ID do erro:** BC36807  
  
### Para corrigir este erro  
  
-   Certifique\-se de que o objeto do qual você está fazendo referência a um atributo é fortemente tipado como <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument>, ou `IEnumerable(Of XElement)`. A seguir está um exemplo:  
  
    ```vb#  
    Dim elem As XElement = <root> <child /> </root> Dim var = elem.<child>  
    ```  
  
## Consulte também  
 [Propriedade do eixo filho XML](/dotnet/visual-basic/language-reference/xml-axis/xml-child-axis-property)   
 [Propriedades do eixo XML](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)