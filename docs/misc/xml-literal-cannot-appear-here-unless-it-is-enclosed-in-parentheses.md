---
title: "Literal XML n&#227;o pode aparecer aqui, a menos que seja colocada entre par&#234;nteses | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31198"
  - "vbc31198"
helpviewer_keywords: 
  - "BC31198"
ms.assetid: 97b16076-39ff-430a-9c65-073d01bcb08e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Literal XML n&#227;o pode aparecer aqui, a menos que seja colocada entre par&#234;nteses
Uma declaração literal XML é usada em uma expressão em um local que é ambíguo para o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador. Ou seja, o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador não pode determinar se o menor\-que caractere \(\<\) serve como um operador de comparação ou o início de um literal XML. O código a seguir fornece um exemplo:  
  
 \[Visual Basic\]  
  
```  
' Generates an error. Dim queryResult = From element In elements _ Where <sample>Value</sample> = "Value" _ Select element  
```  
  
 **ID do erro:** BC31198  
  
### Para corrigir este erro  
  
-   Coloque a declaração literal XML entre parênteses, conforme mostrado no exemplo a seguir:  
  
    ```vb#  
    Dim queryResult = From element In elements _ Where (<sample> Value</sample>) = "Value" _ Select element  
    ```  
  
-   Modifique seu código para se referir a um literal XML existente, conforme mostrado no exemplo a seguir:  
  
    ```vb#  
    Dim queryResult = From element In elements _ Where e.<sample>.Value = "Value" _ Select element  
    ```  
  
## Consulte também  
 [Literais XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [Propriedades do eixo XML](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)