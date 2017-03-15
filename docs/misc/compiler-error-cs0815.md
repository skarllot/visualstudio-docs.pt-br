---
title: "CS0815 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0815"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0815"
ms.assetid: 8f055d34-9ee4-482e-9e79-8b3698c55cb4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0815 de erro do compilador
Não é possível atribuir 'expression' para um local digitada implicitamente  
  
 Uma expressão que é usada como o inicializador para uma variável digitada implicitamente deve ter um tipo. Como as expressões de função anônima, expressões de grupo de método e a expressão literal nula não tem um tipo, eles não são inicializadores apropriados. Uma variável digitada implicitamente não pode ser inicializada com um valor nulo na sua declaração, embora ele mais tarde pode ser atribuído um valor nulo.  
  
### Para corrigir este erro  
  
1.  Forneça um tipo explícito para a variável.  
  
## Exemplo  
 O código a seguir gera CS0815:  
  
```  
// cs0815.cs class Test { public static int Main() { var d = s => -1; // CS0815 var e = (string s) => 0; // CS0815 var p = null;//CS0815 var del = delegate(string a) { return -1; };// CS0815 return -1; } }  
```  
  
## Consulte também  
 [Variáveis locais de tipo implícito](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)