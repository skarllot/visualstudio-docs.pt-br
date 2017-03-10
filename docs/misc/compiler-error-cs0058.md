---
title: "CS0058 de erro do compilador | Microsoft Docs"
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
  - "CS0058"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0058"
ms.assetid: 9535da60-03b9-41ab-93e1-e57b6440fca9
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0058 de erro do compilador
Acessibilidade inconsistente: tipo de retorno 'type' é menos acessível que delegar 'representante'  
  
 Uma construção pública deve retornar um objeto acessível publicamente. Para obter mais informações, consulte [Modificadores de acesso](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
 O exemplo a seguir gera CS0058 porque nenhum modificador de acesso é aplicada aos MyClass e, portanto, ele recebe acessibilidade privada por padrão:  
  
```  
// CS0058.cs class MyClass // try the following line instead // public class MyClass { } public delegate MyClass MyClassDel();   // CS0058 public class A { public static void Main() { } }  
```  
  
## Consulte também  
 [private](/dotnet/csharp/language-reference/keywords/private)