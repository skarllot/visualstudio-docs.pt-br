---
title: "Operandos &#39;If&#39; n&#227;o podem ser argumentos nomeados | Microsoft Docs"
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
  - "bc33105"
  - "vbc33105"
helpviewer_keywords: 
  - "BC33105"
ms.assetid: 596baeb6-a44f-4d92-beb7-06624b60c00d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operandos &#39;If&#39; n&#227;o podem ser argumentos nomeados
Usando argumentos com nome nos operandos do `If` operador não é válido. O exemplo a seguir causa esse erro:  
  
```  
Dim i As Integer Dim result As String ' Not valid. ' result = (If(i > 0, TruePart:="positive", FalsePart:="not positive")  
```  
  
 Isso difere do `IIf` função, permitindo que os argumentos nomeada, conforme mostrado no código a seguir:  
  
```  
' Valid. IIf(i > 0, TruePart:="positive", FalsePart:="not positive")  
```  
  
 **ID do erro:** BC33105  
  
### Para corrigir este erro  
  
-   Remova as atribuições de nome dos operandos, conforme mostrado no código a seguir.  
  
    ```  
    result = If(i > 0, "positive", "not positive")  
    ```  
  
## Consulte também  
 [Operador If](/dotnet/visual-basic/language-reference/operators/if-operator)   
 [Passando argumentos por posição e nome](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)