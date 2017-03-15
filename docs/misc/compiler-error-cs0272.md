---
title: "CS0272 de erro do compilador | Microsoft Docs"
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
  - "CS0272"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0272"
ms.assetid: 16a9aab6-922a-45a3-a0ef-f32e99f3950f
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0272 de erro do compilador
A propriedade ou o indexador 'propriedade\/indexador' não pode ser usado neste contexto porque o acessador set está inacessível  
  
 Esse erro ocorre quando o `set` acessador não é acessível para o código do programa. Para resolver esse erro, aumente a acessibilidade do acessador ou alterar o local de chamada. Para obter mais informações, consulte [Restringindo a acessibilidade aos acessadores](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility).  
  
## Exemplo  
 O exemplo a seguir gera CS0272:  
  
```  
// CS0272.cs public class MyClass { public int Property { get { return 0; } private set { } } } public class Test { static void Main() { MyClass c = new MyClass(); c.Property = 10;      // CS0272 // To resolve, remove the previous line // or use an appropriate modifier on the set accessor. } }  
```