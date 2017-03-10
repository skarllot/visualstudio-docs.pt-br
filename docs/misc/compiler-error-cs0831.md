---
title: "CS0831 de erro do compilador | Microsoft Docs"
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
  - "CS0831"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0831"
ms.assetid: f626a77d-3844-4438-954b-b8201e72b1b5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0831 de erro do compilador
Uma árvore de expressão não pode conter um acesso de base.  
  
 Um meio de acesso base chama uma função que normalmente seria uma chamada de função virtual como uma função não virtual chamada no método da classe base. Isso não é permitido na árvore de expressão em si, mas você pode chamar um método auxiliar em sua classe que invoca o método da classe base.  
  
### Para corrigir este erro  
  
1.  Se você precisar acessar um método da classe base dessa maneira, crie um método auxiliar que chama a classe base e faça com que a árvore de expressão chamar o método auxiliar. Essa técnica é mostrada no código a seguir.  
  
## Exemplo  
 O exemplo a seguir gera CS0831:  
  
```  
// cs0831.cs using System; using System.Linq; using System.Linq.Expressions; public class A { public virtual int BaseMethod() { return 1; } } public class C : A { public override int BaseMethod() { return 2; } public int Test(C c) { Expression<Func<int>> e = () => base.BaseMethod(); // CS0831 // Try the following line instead, // along with the BaseAccessHelper method. // Expression<Func<int>> e2 = () => BaseAccessHelper(); return 1; } // Uncomment to call from e2 expression above. // int BaseAccessHelper() // { //     return base.BaseMethod(); // } }   
```