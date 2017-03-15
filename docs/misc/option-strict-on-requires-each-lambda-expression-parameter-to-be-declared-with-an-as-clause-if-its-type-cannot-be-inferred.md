---
title: "Option Strict On requer que cada par&#226;metro de express&#227;o lambda seja declarado com uma cl&#225;usula &#39;As&#39; se seu tipo n&#227;o pode ser inferido | Microsoft Docs"
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
  - "bc36642"
  - "vbc36642"
helpviewer_keywords: 
  - "BC36642"
ms.assetid: 2aaa62b8-49c9-4ae8-b0f5-08e3f0b5ad10
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On requer que cada par&#226;metro de express&#227;o lambda seja declarado com uma cl&#225;usula &#39;As&#39; se seu tipo n&#227;o pode ser inferido
Você declarou um parâmetro em uma expressão lambda sem usar um `As` cláusula, com `Option Strict` em.  
  
```  
' Not valid when Option Strict is on. ' Dim increment1 = Function (n) n + 1  
```  
  
 A declaração anterior é válida se o tipo de `n` pode ser inferido. Por exemplo, se você estiver atribuindo a expressão lambda para uma função delegar, `Del`:  
  
```  
Delegate Function Del(ByVal p As Integer) As Integer  
```  
  
 Agora o tipo de `n` pode ser inferido a partir do parâmetro `p`:  
  
```  
Dim increment2 as Del = Function(n) n + 1  
```  
  
 **ID do erro:** BC36642  
  
### Para corrigir este erro  
  
-   Adicione um `As` cláusula à declaração de parâmetro:  
  
    ```  
    Dim increment3 = Function (n As Integer) n + 1  
    ```  
  
## Consulte também  
 [Expressões lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)