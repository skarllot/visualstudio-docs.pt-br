---
title: "N&#227;o &#233; poss&#237;vel inferir um tipo comum para o segundo e terceiro operandos do operador &#39;If&#39; | Microsoft Docs"
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
  - "vbc33106"
  - "bc33106"
helpviewer_keywords: 
  - "BC33106"
ms.assetid: 793eed88-a9f9-43e3-b657-c16795ecbbcc
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel inferir um tipo comum para o segundo e terceiro operandos do operador &#39;If&#39;
Não é possível inferir um tipo comum para o segundo e terceiro operandos do operador 'If'. Um deve ter uma conversão de ampliação para a outra.  
  
 Quando o `If` operador é chamado com três argumentos, deve haver uma conversão de ampliação entre o segundo e terceiro argumentos. Por exemplo, porque não há uma conversão de ampliação em ambas as direções entre `Integer` e `String`, o código a seguir causa esse erro.  
  
```vb#  
Dim divisor = 3  
' Not valid.  
' Console.WriteLine(If(divisor <> 0, number \ divisor, "Division by zero"))  
```  
  
 **ID do erro:** BC33106  
  
### Para corrigir este erro  
  
-   Forneça uma conversão explícita para um dos operandos, se for possível no seu código.  
  
-   Use uma construção de condição diferente, como um `If...Then...Else` instrução.  
  
## Consulte também  
 [Operador If](/dotnet/visual-basic/language-reference/operators/if-operator)   
 [Instrução If...Then...Else](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)   
 [Conversões de Widening e Narrowing](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)