---
title: "CS1953 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "10/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1953"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1953"
ms.assetid: b8af5eed-0f3b-4258-b4e2-f5d184288239
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1953 de erro do compilador
Uma árvore de expressão lambda não pode conter um grupo de método.  
  
 Uma chamada de método requer o `()` operador. O nome do método sem esse operador refere\-se ao grupo de método, que é o conjunto de todos os métodos sobrecarregados com esse nome.  
  
### Para corrigir este erro  
  
1.  Se você deve chamar o método, adicione o `()` operador.  
  
## Exemplo  
 O exemplo a seguir gera CS1953:  
  
```  
// cs1953.cs using System; using System.Linq.Expressions; class CS1953 { public static void Main() { double num = 10; Expression<Func<bool>> testExpr = () => num.GetType is int; // CS1953 } }  
```