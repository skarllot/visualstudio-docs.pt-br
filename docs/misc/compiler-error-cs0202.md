---
title: "CS0202 de erro do compilador | Microsoft Docs"
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
  - "CS0202"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0202"
ms.assetid: 7088850f-c206-4b95-9586-a0fa3d876c0c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0202 de erro do compilador
foreach requer que o tipo de retorno 'type' de ' tipo. GetEnumerator \(\) ' deve ter um método MoveNext público adequado e a propriedade Current pública  
  
 Um <xref:System.Collections.IEnumerable.GetEnumerator%2A> função, usado para habilitar o uso de instruções de foreach não pode retornar um ponteiro ou matriz; ele deve retornar uma instância de uma classe que é capaz de atuar como um enumerador. Os requisitos apropriados para servir como um enumerador incluem uma propriedade pública de atual e um método MoveNext público.  
  
> [!NOTE]
>  No c\# 2.0, o compilador gerará automaticamente atual e MoveNext para você. Para obter mais informações, consulte o exemplo de código [Interfaces genéricas](/dotnet/csharp/programming-guide/generics/generic-interfaces).  
  
 O exemplo a seguir gera CS0202:  
  
```  
// CS0202.cs public class C1 { public int Current { get { return 0; } } public bool MoveNext () { return false; } public static implicit operator C1 (int c1) { return 0; } } public class C2 { public int Current { get { return 0; } } public bool MoveNext () { return false; } public C1[] GetEnumerator () // try the following line instead // public C1 GetEnumerator () { return null; } } public class MainClass { public static void Main () { C2 c2 = new C2(); foreach (C1 x in c2)   // CS0202 { System.Console.WriteLine(x.Current); } } }  
```