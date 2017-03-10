---
title: "CS0535 de erro do compilador | Microsoft Docs"
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
  - "CS0535"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0535"
ms.assetid: 282ed5d6-acb7-445b-999f-27a973ccc0b5
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0535 de erro do compilador
'class' não implementa membro de interface 'member'  
  
 Um [classe](/dotnet/csharp/language-reference/keywords/class) derivado de um [interface](/dotnet/csharp/language-reference/keywords/interface), mas a classe não implementou um ou mais dos membros da interface. Uma classe deve implementar todos os membros das interfaces do qual ele deriva ou então ser declarado `abstract`.  
  
## Exemplo  
 O exemplo a seguir gera CS0535.  
  
```  
// CS0535.cs public interface A { void F(); } public class B : A {}   // CS0535 A::F is not implemented // OK public class C : A { public void F() {} public static void Main() {} }  
```  
  
## Exemplo  
 O exemplo a seguir gera CS0535.  
  
```  
// CS0535_b.cs using System; class C : IDisposable {}   // CS0535 // OK class D : IDisposable { void IDisposable.Dispose() {} public void Dispose() {} static void Main() { using (D d = new D()) {} } }  
```