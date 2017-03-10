---
title: "CS1100 de erro do compilador | Microsoft Docs"
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
  - "CS1100"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1100"
ms.assetid: ea233371-36b6-49ae-a98c-a00ee3b79e53
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1100 de erro do compilador
O método 'name' tem um modificador de parâmetro 'this' que não está no primeiro parâmetro.  
  
 O `this` modificador é permitido apenas no primeiro parâmetro de um método, que indica para o compilador que o método é um método de extensão.  
  
### Para corrigir este erro  
  
1.  Remover o `this` modificador de todos, exceto o primeiro parâmetro do método.  
  
## Exemplo  
 O código a seguir gera CS1100 porque um `this` parâmetro está modificando o segundo parâmetro:  
  
```  
// cs1100.cs static class Test { static void ExtMethod(int i, this Test c) // CS1100 { } }  
```  
  
## Consulte também  
 [Métodos de extensão](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)