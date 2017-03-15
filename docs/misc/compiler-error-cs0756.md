---
title: "CS0756 de erro do compilador | Microsoft Docs"
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
  - "CS0756"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0756"
ms.assetid: 847b20b0-bbf0-43a2-8728-4b54cb3d9cd6
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0756 de erro do compilador
Um método parcial não pode ter várias declarações de definição.  
  
 A declaração de definição de um método parcial é a parte que especifica a assinatura do método, mas não a implementação \(corpo do método\). Um método parcial deve ter exatamente uma declaração de definição para cada assinatura exclusiva. Cada versão sobrecarregada de um método parcial deve ter sua própria definição de declaração.  
  
### Para corrigir este erro  
  
1.  Remova todas exceto uma declaração de definição do método parcial.  
  
## Exemplo  
  
```  
// cs0756.cs using System; public partial class C { partial void Part(); partial void Part(); // CS0756 public static int Main() { return 1; } }  
```  
  
## Consulte também  
 [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)