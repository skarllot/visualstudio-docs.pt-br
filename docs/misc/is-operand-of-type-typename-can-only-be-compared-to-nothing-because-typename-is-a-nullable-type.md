---
title: "O operando &#39;Is&#39; do tipo &#39;typename&#39; s&#243; pode ser comparado a &#39;Nothing&#39;, porque &#39;typename&#39; &#233; um tipo anul&#225;vel | Microsoft Docs"
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
  - "vbc32127"
  - "bc32127"
helpviewer_keywords: 
  - "BC32127"
ms.assetid: 68b745b5-8605-4bf3-a6ec-69e67b3cff2d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O operando &#39;Is&#39; do tipo &#39;typename&#39; s&#243; pode ser comparado a &#39;Nothing&#39;, porque &#39;typename&#39; &#233; um tipo anul&#225;vel
Uma variável declarada como anulável foi comparada com uma expressão que `Nothing` usando o `Is` operador.  
  
 **ID do erro:** BC32127  
  
### Para corrigir este erro  
  
1.  Para comparar um tipo anulável com uma expressão que `Nothing` usando o `Is` operador, chame o `GetType` método no tipo anulável e compare o resultado para a expressão, conforme mostrado no exemplo a seguir.  
  
    ```vb#  
    Dim number? As Integer = 5 If number IsNot Nothing Then If number.GetType() Is Type.GetType("System.Int32") Then End If End If  
    ```  
  
## Consulte também  
 [Tipos de valor que permitem valor nulo](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)   
 [Operador Is](/dotnet/visual-basic/language-reference/operators/is-operator)