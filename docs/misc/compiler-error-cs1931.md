---
title: "CS1931 de erro do compilador | Microsoft Docs"
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
  - "CS1931"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1931"
ms.assetid: c0071c3d-ae11-4073-87df-508150daef68
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1931 de erro do compilador
O intervalo variável 'variável' está em conflito com uma declaração anterior de 'variável'.  
  
 A declaração de uma variável de intervalo, assim como cada declaração, deve ter um identificador que é exclusivo no espaço de declaração da variável.  
  
### Para corrigir este erro  
  
1.  Dê à variável de intervalo um nome exclusivo.  
  
## Exemplo  
 O código a seguir gera CS1931 porque o identificador `x` é usado como uma variável local no `Main` e como a variável de intervalo na expressão de consulta:  
  
```  
// cs1931.cs class Test { static void Main() { int x = 1; var y = from x in Enumerable.Range(1, 100) // CS1931 select x; } }  
```  
  
## Consulte também  
 [Expressões de consulta LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)