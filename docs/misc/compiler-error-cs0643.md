---
title: "CS0643 de erro do compilador | Microsoft Docs"
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
  - "CS0643"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0643"
ms.assetid: beae30ff-15c2-413f-8f5c-504cdba2e57a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0643 de erro do compilador
argumento de atributo nomeado duplicado 'arg'  
  
 Um parâmetro, `arg`, em um atributo definido pelo usuário foi especificado duas vezes. Para obter mais informações, consulte [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Exemplo  
 O exemplo a seguir gera CS0643:  
  
```  
// CS0643.cs using System; using System.Runtime.InteropServices; [AttributeUsage(AttributeTargets.Class)] public class MyAttribute : Attribute { public MyAttribute() { } public int x; } [MyAttribute(x = 5, x = 6)]   // CS0643, error setting x twice // try the following line instead // [MyAttribute(x = 5)] class MyClass { } public class MainClass { public static void Main () { } }  
```