---
title: "CS1932 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1932"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1932"
ms.assetid: fc927899-2d35-4d47-9ae9-8fc99295bb66
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1932 de erro do compilador
Não é possível atribuir 'expression' a uma variável de intervalo.  
  
 O compilador deve ser capaz de inferir o tipo de uma variável de intervalo, se ele foi introduzido em um `from` cláusula ou um `let` cláusula. Ele não pode ser nulo porque null não é um tipo, e ele não pode ser atribuído com uma expressão de um tipo não é segura.  
  
### Para corrigir este erro  
  
-   Remova a atribuição não é válida.  
  
-   Converter a expressão para um tipo permitido explicitamente  
  
## Exemplo  
 O código a seguir gera CS1932 porque o tipo da variável de intervalo não pode ser inferido. Converta o valor para o tipo desejado para corrigir o erro, conforme mostrado no exemplo a seguir.  
  
```  
// CS1932.cs using System.Linq; class Test { static void Main() { var x = from i in Enumerable.Range(1, 100) let k = null // CS1932 // Try the following line instead. let k = (string) null select i; } }  
```  
  
## Consulte também  
 [Expressões de consulta LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)