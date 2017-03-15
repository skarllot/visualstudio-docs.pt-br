---
title: "CS0271 de erro do compilador | Microsoft Docs"
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
  - "CS0271"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0271"
ms.assetid: eadc9fb5-7770-4ec4-94f6-3c7cf37eec06
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0271 de erro do compilador
A propriedade ou o indexador 'propriedade\/indexador' não pode ser usado neste contexto porque o acessador get está inacessível  
  
 Esse erro ocorre quando você tenta acessar um inacessível `get` acessador. Para resolver esse erro, aumente a acessibilidade do acessador ou alterar o local de chamada. Para obter mais informações, consulte [acessibilidade do acessador](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility) e [Propriedades](/dotnet/csharp/programming-guide/classes-and-structs/properties).  
  
 O exemplo a seguir gera CS0271:  
  
```  
// CS0271.cs public class MyClass { public int Property { private get { return 0; } set { } } public int Property2 { get { return 0; } set { } } } public class Test { public static void Main(string[] args) { MyClass c = new MyClass(); int a = c.Property;   // CS0271 int b = c.Property2;   // OK } }  
```