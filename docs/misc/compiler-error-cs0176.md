---
title: "CS0176 de erro do compilador | Microsoft Docs"
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
  - "CS0176"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0176"
ms.assetid: 783c13d8-5ac3-4aeb-bd63-0468cb05550d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0176 de erro do compilador
Membro estático 'member' não pode ser acessado com uma referência de instância; Qualifique\-o com um nome de tipo  
  
 Somente um nome de classe pode ser usado para qualificar um [estático](/dotnet/csharp/language-reference/keywords/static) variável; um nome de instância não pode ser um qualificador. Para obter mais informações, consulte [Classes static e membros de classes static](/dotnet/csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members).  
  
 O exemplo a seguir gera CS0176:  
  
```  
// CS0176.cs public class MyClass2 { public static int num; } public class Test { public static void Main() { MyClass2 mc2 = new MyClass2(); int i = mc2.num;   // CS0176 // try the following line instead // int i = MyClass2.num; } }  
  
```