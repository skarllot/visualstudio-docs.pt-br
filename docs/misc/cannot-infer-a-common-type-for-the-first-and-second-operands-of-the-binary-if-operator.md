---
title: "N&#227;o &#233; poss&#237;vel inferir um tipo comum para o primeiro e o segundo operando do operador &#39;If&#39; bin&#225;ria | Microsoft Docs"
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
  - "vbc33110"
  - "bc33110"
helpviewer_keywords: 
  - "BC33110"
ms.assetid: f46873aa-f6cd-4cc9-9e8e-e668bddf0980
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel inferir um tipo comum para o primeiro e o segundo operando do operador &#39;If&#39; bin&#225;ria
Não é possível inferir um tipo comum para o primeiro e o segundo operando do operador 'If' binário. Um deve ter uma conversão de ampliação para a outra.  
  
 O binário `If` operador requer uma conversão de ampliação entre um dos argumentos e o outro argumento. Por exemplo, porque não há uma conversão de ampliação em ambas as direções entre `Integer` e `String`, o código a seguir causa esse erro.  
  
```vb#  
Dim first? As Integer  
Dim second As String = "First is Nothing"  
'' Not valid.  
' Console.WriteLine(If(first, second))  
```  
  
 **ID do erro:** BC33110  
  
### Para corrigir este erro  
  
-   Forneça uma conversão explícita para um dos operandos, se for possível no seu código:  
  
    ```  
    Console.WriteLine(If(first, CInt(second)))   
    ```  
  
-   Reescreva o código usando uma construção condicional diferente.  
  
    ```  
    If first IsNot Nothing Then  
        Console.WriteLine(first)  
    Else  
        Console.WriteLine(second)  
    End If  
    ```  
  
## Consulte também  
 [Operador If](/dotnet/visual-basic/language-reference/operators/if-operator)   
 [Conversões de Widening e Narrowing](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Instrução If...Then...Else](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)