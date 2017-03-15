---
title: "CS1520 de erro do compilador | Microsoft Docs"
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
  - "CS1520"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1520"
ms.assetid: 1aeeee83-52a6-45dc-b197-a9a6de3a220c
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1520 de erro do compilador
Método deve ter um tipo de retorno  
  
 Um método que é declarado em uma classe, estrutura ou interface deve ter um tipo de retorno explícito. No exemplo a seguir, o método quadrado tem um valor de retorno [seqüência](/dotnet/csharp/language-reference/keywords/string):  
  
```  
class Test { string IntToString(int i) { return i.ToString(); } }  
```  
  
 O exemplo a seguir gera CS1520:  
  
```  
// CS1520a.cs public class x { // Method declaration missing a return type MyMethod()   // CS1520 {} // Add the desired return type: // void MyMethod2() // { } public static void Main() { } }  
```  
  
 Como alternativa, esse erro pode ser encontrado durante a ocorrência do nome de um construtor é diferente da declaração de classe ou estrutura, como no exemplo a seguir. Porque o nome não é exatamente o mesmo que o nome da classe, o compilador interpreta como um método regular, não um construtor e produz o erro:  
  
```  
// CS1520b.cs public class Class1 { // Should be Class1, not class1 public class1()   // CS1520 { } static void Main() { } }  
```  
  
## Consulte também  
 [Métodos](/dotnet/csharp/programming-guide/classes-and-structs/methods)   
 [Construtores](/dotnet/csharp/programming-guide/classes-and-structs/constructors)