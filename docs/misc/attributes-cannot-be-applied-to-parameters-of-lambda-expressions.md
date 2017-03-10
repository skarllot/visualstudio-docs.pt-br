---
title: "Atributos n&#227;o podem ser aplicados aos par&#226;metros de express&#245;es lambda | Microsoft Docs"
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
  - "vbc36634"
  - "bc36634"
helpviewer_keywords: 
  - "BC36634"
ms.assetid: ed751d8d-11b7-4210-97e0-0319edff8c34
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Atributos n&#227;o podem ser aplicados aos par&#226;metros de express&#245;es lambda
Você aplicou um atributo para um parâmetro em uma definição de expressão lambda, que não é suportado. O código a seguir causa esse erro.  
  
```vb#  
Sub LambaAttribute()  
    ' Not valid.  
    Dim add1 = _  
    Function(<System.Runtime.InteropServices.InAttribute()> m As Integer) _  
                   m + 1  
End Sub  
```  
  
 **ID do erro:** BC36634  
  
### Para corrigir este erro  
  
-   Remova o atributo ou considere revisar seu código, alterando a expressão lambda para uma função normal.  
  
## Consulte também  
 <xref:System.Runtime.InteropServices.InAttribute>   
 [Expressões lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [NÃO está em compilação: Atributos no Visual Basic](http://msdn.microsoft.com/pt-br/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)