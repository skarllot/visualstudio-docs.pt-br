---
title: "CS0736 de erro do compilador | Microsoft Docs"
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
  - "CS0736"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0736"
ms.assetid: 06b14feb-81d5-495f-ab2d-6dc3f5e7216f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0736 de erro do compilador
'type name' não implementa membro de interface 'nome do membro'. nome do método não pode implementar um membro de interface porque é estático.  
  
 Esse erro é gerado quando um método estático é declarado implicitamente ou explicitamente como uma implementação de um membro da interface.  
  
### Para corrigir este erro  
  
-   Remover o [estático](/dotnet/csharp/language-reference/keywords/static) modificador da declaração de método.  
  
-   Altere o nome do método de interface.  
  
-   Redefina o tipo recipiente para que ele não herda da interface.  
  
## Exemplo  
 O código a seguir gera CS0736 porque `Program.testMethod` é declarado como estático:  
  
```  
// cs0736.cs namespace CS0736 { interface ITest { int testMethod(int x); } class Program : ITest // CS0736 { public static int testMethod(int x) { return 0; } // Try the following line instead. // public int testMethod(int x) { return 0; } public static void Main() { } } }  
```  
  
## Consulte também  
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)