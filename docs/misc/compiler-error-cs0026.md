---
title: "CS0026 de erro do compilador | Microsoft Docs"
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
  - "CS0026"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0026"
ms.assetid: 8767fbc1-8ba7-4e88-a9f9-7e620411882b
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0026 de erro do compilador
Palavra\-chave 'this' não é válida em uma propriedade estática, um método estático ou um inicializador de campo estático  
  
 O [this](/dotnet/csharp/language-reference/keywords/this) palavra\-chave se refere a um objeto, que é uma instância de um tipo. Como os métodos estáticos são independentes de qualquer instância da classe recipiente, a palavra\-chave "this" não faz sentida e, portanto, não é permitida. Para obter mais informações, consulte [Classes static e membros de classes static](/dotnet/csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members) e [Objetos](/dotnet/csharp/programming-guide/classes-and-structs/objects).  
  
## Exemplo  
 O exemplo a seguir gera CS0026:  
  
```  
// CS0026.cs public class A { public static int i = 0; public static void Main() { // CS0026 this.i = this.i + 1; // Try the following line instead: // i = i + 1; } }  
```