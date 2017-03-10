---
title: "CS0764 de erro do compilador | Microsoft Docs"
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
  - "CS0764"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0764"
ms.assetid: 76a64149-49d8-40ea-a976-03835d8fb7eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0764 de erro do compilador
As duas declarações de métodos parciais devem ser inseguras ou nenhuma delas deve ser não segura  
  
 Um método parcial consiste em uma declaração de definição \(assinatura\) e uma declaração de implementação opcional \(corpo\). Se a declaração de definição de `unsafe` modificador, a declaração de implementação também deve tê\-lo. Por outro lado, se a declaração de implementação tem o `unsafe` modificador, a declaração de definição deve também.  
  
### Para corrigir este erro  
  
1.  Supondo que a declaração de definição estiver correta, adicionar ou remover o `unsafe` modificador da declaração de implementação para coincidir com a declaração de definição.  
  
## Exemplo  
  
```  
// cs0764.cs //  Compile with: /target:library /unsafe public partial class C { partial void Part(); unsafe partial void Part() //CS0764 { } public static int Main() { return 1; } }  
```  
  
## Consulte também  
 [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)