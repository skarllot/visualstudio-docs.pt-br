---
title: "CS0314 de erro do compilador | Microsoft Docs"
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
  - "CS0314"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0314"
ms.assetid: 12f68f51-0568-4e80-b0fd-15899807477d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0314 de erro do compilador
O tipo 'type1' não pode ser usado como tipo parâmetro 'name' no genérico tipo ou método 'nome'. Não há nenhuma conversão boxing ou conversão de parâmetro de tipo de 'type1' em 'type2'.  
  
 Quando um tipo genérico usa um parâmetro de tipo é restrito, a nova classe também deve atender a essas mesmas restrições.  
  
### Para corrigir este erro  
  
1.  No exemplo a seguir, adicione `where T : ClassConstraint` a classe `B`.  
  
## Exemplo  
 O código a seguir gera CS0314:  
  
```  
// cs0314.cs // Compile with: /target:library public class ClassConstraint { } public class A<T> where T : ClassConstraint { } public class B<T> : A<T> //CS0314 { } // Try using this instead. public class C<T> : A<T> where T : ClassConstraint { }  
```  
  
## Consulte também  
 [Restrições a parâmetros de tipo](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)