---
title: "CS0403 de erro do compilador | Microsoft Docs"
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
  - "CS0403"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0403"
ms.assetid: 6e5d55ce-d6bf-419d-aded-aaa2e5963bb6
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0403 de erro do compilador
Não é possível converter nulo para o tipo de parâmetro 'name' porque ela pode ser um tipo de valor não nulo. Considere usar default\('T'\).  
  
 É possível atribuir null para o tipo desconhecido chamado porque ele pode ser um tipo de valor, que não permite a atribuição de nula. Se sua classe genérica não deve aceitar tipos de valor, use a restrição de tipo de classe. Se ele pode aceitar tipos de valor, como os tipos internos, você poderá substituir a atribuição para nulo com a expressão `default(T)`, conforme mostrado no exemplo a seguir.  
  
## Exemplo  
 O exemplo a seguir gera CS0403.  
  
```  
// CS0403.cs // compile with: /target:library class C<T> { public void f() { T t = null;  // CS0403 T t2 = default(T);   // OK } } class D<T> where T : class { public void f() { T t = null;  // OK } }  
```