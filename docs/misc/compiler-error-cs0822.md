---
title: "CS0822 de erro do compilador | Microsoft Docs"
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
  - "CS0822"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0822"
ms.assetid: 519091be-2332-4df4-acd9-e3b633966b3d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0822 de erro do compilador
Locais digitados implicitamente não podem ser constantes  
  
 Variáveis de locais digitadas implicitamente só são necessárias para o armazenamento de tipos anônimos. Em outros casos, eles são apenas uma conveniência. Se o valor da variável nunca muda, apenas dê um tipo explícito. Tentativa de usar o `readonly` modificador com um local digitada implicitamente irá gerar CS0106.  
  
### Para corrigir este erro  
  
1.  Se você precisar que a variável seja constante ou `readonly`, dê a ele um tipo explícito.  
  
## Exemplo  
 O código a seguir gera CS0822:  
  
```  
// cs0822.cs class A { public static int Main() { const var x = 0; // CS0822.cs return -1; } }  
```  
  
## Consulte também  
 [Variáveis locais de tipo implícito](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)