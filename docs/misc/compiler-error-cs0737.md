---
title: "CS0737 de erro do compilador | Microsoft Docs"
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
  - "CS0737"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0737"
ms.assetid: d2247770-5546-46f2-a01d-8e2ebfcbb859
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0737 de erro do compilador
'type name' não implementa membro de interface 'nome do membro'. 'nome do método' não pode implementar um membro de interface, pois não é público.  
  
 Um método que implementa um membro de interface deve ter acessibilidade pública. Todos os membros de interface são `public`.  
  
### Para corrigir este erro  
  
1.  Adicionar o [pública](/dotnet/csharp/language-reference/keywords/public) modificador de acesso para o método.  
  
## Exemplo  
 O código a seguir gera CS0737:  
  
```  
// cs0737.cs interface ITest { // Default access of private with no modifier. int Return42(); // Try the following line instead. // public int Return42(); } struct Struct1 : ITest // CS0737 { int Return42() { return (42); } } public class Test { public static int Main(string[] args) { Struct1 s1 = new Struct1(); return (1); } }  
```  
  
## Consulte também  
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)