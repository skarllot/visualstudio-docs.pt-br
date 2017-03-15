---
title: "Par&#226;metro &#39;ByRef&#39; &#39;&lt; parametername &gt;&#39; n&#227;o pode ser usado em uma express&#227;o lambda | Microsoft Docs"
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
  - "bc36639"
  - "vbc36639"
helpviewer_keywords: 
  - "BC36639"
ms.assetid: 5913f9b6-2929-4c05-8dd1-00b10fcd5a83
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Par&#226;metro &#39;ByRef&#39; &#39;&lt; parametername &gt;&#39; n&#227;o pode ser usado em uma express&#227;o lambda
Uma expressão lambda declarada dentro de um `Sub` ou função não pode usar qualquer `ByRef` parâmetros de que `Sub` ou função. Por exemplo, o código a seguir irá causar esse erro porque o `ByRef` parâmetro `n` é usado na expressão lambda.  
  
```  
'' Not valid.   
'Sub ExampleSub(ByRef n As Integer)  
  
'    Dim lambda = Function(p As Integer) p + n  
  
'End Sub  
```  
  
 **ID do erro:** BC36639  
  
### Para corrigir este erro  
  
-   Atribuir o `ByRef` parâmetro para uma variável local e use a variável local na expressão lambda, conforme mostrado no código a seguir:  
  
    ```  
    Sub ExampleSub(ByRef n As Integer)  
  
        Dim temp = n  
        Dim lambda = Function(p As Integer) p + temp  
  
    End Sub  
    ```  
  
## Consulte também  
 [Expressões lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)