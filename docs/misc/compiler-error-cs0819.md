---
title: "CS0819 de erro do compilador | Microsoft Docs"
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
  - "CS0819"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0819"
ms.assetid: a5369e03-eb7d-4c88-b390-51304bd8d1ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0819 de erro do compilador
Locais digitados implicitamente não podem ter vários declaradores.  
  
 Vários declaradores são permitidos em declarações de tipo explícitas, mas não com variáveis digitadas implicitamente.  
  
### Para corrigir este erro  
  
1.  Declarar e atribuir um valor para cada variável local digitada implicitamente em uma linha separada.  
  
## Exemplo  
 O código a seguir gera CS0819:  
  
```  
// cs0819.cs class A { public static int Main() { var a = 3, b = 2; // CS0819 return -1; } }  
```  
  
## Consulte também  
 [Variáveis locais de tipo implícito](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)