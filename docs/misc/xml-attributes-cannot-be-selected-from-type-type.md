---
title: "Atributos XML n&#227;o podem ser selecionados do tipo &#39;type&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36808"
  - "vbc36808"
helpviewer_keywords: 
  - "BC36808"
ms.assetid: 76b2605c-3d9b-4e56-ba3f-99c60c668290
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Atributos XML n&#227;o podem ser selecionados do tipo &#39;type&#39;
Um atributo XML foi referenciado por um objeto que não é do tipo <xref:System.Xml.Linq.XElement> ou `IEnumerable(Of XElement)`. Para obter mais informações, consulte [Propriedade de eixo do atributo XML](/dotnet/visual-basic/language-reference/xml-axis/xml-attribute-axis-property).  
  
```vb#  
' Generates an error. Dim var = "sample text".@attr  
```  
  
 **ID do erro:** BC36808  
  
### Para corrigir este erro  
  
-   Certifique\-se de que o objeto do qual você está fazendo referência a um atributo é fortemente tipado como <xref:System.Xml.Linq.XElement> ou `IEnumerable(Of XElement)`. A seguir está um exemplo:  
  
    ```vb#  
    Dim elem As XElement = <root attr="value"/> Dim var = elem.@attr  
    ```  
  
## Consulte também  
 [Propriedade de eixo do atributo XML](/dotnet/visual-basic/language-reference/xml-axis/xml-attribute-axis-property)   
 [Propriedades do eixo XML](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)