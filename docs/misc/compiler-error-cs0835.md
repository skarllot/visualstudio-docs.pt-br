---
title: "CS0835 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0835"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0835"
ms.assetid: 593c26f6-6d82-49a6-8ace-4d29dd9f5fbe
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0835 de erro do compilador
Não é possível converter lambda em uma árvore de expressões cujo argumento 'tipo' não é um tipo delegado.  
  
 Se uma expressão lambda é convertida em uma árvore de expressão, a árvore de expressão deve ter um tipo de delegado para seu argumento. Além disso, a expressão lambda deve ser conversível para o tipo de delegado.  
  
### Para corrigir este erro  
  
1.  Altere o parâmetro de tipo de `int` para um tipo delegado, por exemplo `Func<int,int>`.  
  
## Exemplo  
 O exemplo a seguir gera CS0835:  
  
```  
// cs0835.cs using System; using System.Linq; using System.Linq.Expressions; public class C { public static int Main() { Expression<int> e = x => x + 1; // CS0835 // Try the following line instead. // Expression<Func<int,int>> e2 = x => x + 1; return 1; } }  
```