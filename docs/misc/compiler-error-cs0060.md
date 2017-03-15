---
title: "CS0060 de erro do compilador | Microsoft Docs"
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
  - "CS0060"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0060"
ms.assetid: ae6d4fb7-5ff9-4883-82c3-f55b190f439a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0060 de erro do compilador
Acessibilidade inconsistente: classe base 'class1' é menos acessível que a classe 'class2'  
  
 Acessibilidade de classe deve ser consistente entre a classe base e a classe herdada.  
  
 O exemplo a seguir gera CS0060:  
  
```  
// CS0060.cs class MyClass // try the following line instead // public class MyClass { } public class MyClass2 : MyClass   // CS0060 { public static void Main() { } }  
```  
  
## Consulte também  
 [Modificadores de acesso](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)