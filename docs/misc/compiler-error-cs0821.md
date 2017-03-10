---
title: "CS0821 de erro do compilador | Microsoft Docs"
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
  - "CS0821"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0821"
ms.assetid: ef449115-93e8-4fa5-848a-d30dc7f68ddf
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0821 de erro do compilador
Locais digitados implicitamente não podem ser corrigidos.  
  
 Não há suporte para variáveis de locais digitadas implicitamente e tipos anônimos no `fixed` contexto.  
  
### Para corrigir este erro  
  
1.  Remova o `fixed` modificador de variável ou pessoa dar à variável um tipo explícito.  
  
## Exemplo  
 O código a seguir gera CS0821:  
  
```  
class A { static int x; public static int Main() { unsafe { fixed (var p = &x) { } } return -1; } }  
```  
  
## Consulte também  
 [Variáveis locais de tipo implícito](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)