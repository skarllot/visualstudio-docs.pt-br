---
title: "CS1954 de erro do compilador | Microsoft Docs"
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
  - "CS1954"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1954"
ms.assetid: bdec399e-c43d-46d3-a01b-ef3572786fe5
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1954 de erro do compilador
O melhor método sobrecarregado correspondência 'method' para o elemento do inicializador de coleção não pode ser usado. Métodos de 'Add' de inicializador de coleção não podem ter ref ou parâmetros de saída.  
  
 Uma classe de coleção ser inicializado usando um inicializador de coleção, a classe deve ter um `public` `Add` método que não seja um `ref` ou `out` parâmetro.  
  
### Para corrigir este erro  
  
-   Se você pode modificar o código\-fonte da classe de coleção, forneça um `Add` método que não tem um `ref` ou `out` parâmetro.  
  
-   Se você não pode modificar a classe de coleção, inicializá\-lo com os construtores que ele fornece. Você não pode usar um inicializador de coleção com ele.  
  
## Exemplo  
 O exemplo a seguir produz CS1954 porque a sobrecarga disponível apenas o `Add` lista em `MyList` tem um `ref` parâmetro.  
  
```  
// cs1954.cs using System.Collections.Generic; class MyList<T> : IEnumerable<T> { List<T> _list; public void Add(ref T item) { _list.Add(item); } public System.Collections.Generic.IEnumerator<T> GetEnumerator() { int index = 0; T current = _list[index]; while (current != null) { yield return _list[index++]; } } System.Collections.IEnumerator System.Collections.IEnumerable.GetEnumerator() { return GetEnumerator(); } } public class MyClass { public string tree { get; set; } } class Program { static void Main(string[] args) { MyList<MyClass> myList = new MyList<MyClass> { new MyClass { tree = "maple" } }; // CS1954 } }  
  
```  
  
## Consulte também  
 [Inicializadores de objeto e coleção](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)