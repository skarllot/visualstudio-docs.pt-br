---
title: "Express&#227;o lambda n&#227;o pode ser convertida em &#39;&lt; typename &gt;&#39; porque &#39;&lt; typename &gt;&#39; n&#227;o &#233; um tipo delegado | Microsoft Docs"
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
  - "bc36625"
  - "vbc36625"
helpviewer_keywords: 
  - "BC36625"
ms.assetid: c03634d4-d831-4f8c-b6ab-566465968e4d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Express&#227;o lambda n&#227;o pode ser convertida em &#39;&lt; typename &gt;&#39; porque &#39;&lt; typename &gt;&#39; n&#227;o &#233; um tipo delegado
Expressões lambda podem ser usadas onde os delegados são válidos. Eles podem ser convertidos para tipos delegados compatível, mas não para qualquer outro tipo. Por exemplo, você pode definir um tipo de delegado e atribuir uma expressão lambda para ele ou enviar uma expressão lambda como argumento para um <xref:System.Func%601> parâmetro. Esses exemplos são mostrados no código a seguir.  
  
```vb#  
Module Module1 Delegate Function FunDel(ByVal m As Integer) As Boolean Sub Main() ' Assign a lambda expression to a function delegate. Dim negative As FunDel = Function(n As Integer) n < 0 Console.WriteLine(negative(-3)) ' Send a lambda as the argument to a delegate parameter. Dim numbers() As Integer = {3, 4, 2, 8, 1, 0, 9, 13, 42} Dim evens = numbers.Where(Function(n) n Mod 2 = 0) For Each even In evens Console.WriteLine(even) Next End Sub End Module  
```  
  
 **ID do erro:** BC36625  
  
## Consulte também  
 [Expressões lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)