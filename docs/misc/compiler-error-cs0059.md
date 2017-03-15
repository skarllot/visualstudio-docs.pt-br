---
title: "CS0059 de erro do compilador | Microsoft Docs"
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
  - "CS0059"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0059"
ms.assetid: 25a8624b-7f7b-4487-ba80-413d57f9132b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0059 de erro do compilador
Acessibilidade inconsistente: tipo de parâmetro 'type' é menos acessível que delegar 'representante'  
  
 O tipo de retorno e cada um dos tipos referenciados na lista de parâmetros formais de um método devem ser pelo menos tão acessíveis quanto o método em si. Para obter mais informações, consulte [Modificadores de acesso](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
## Exemplo  
 O exemplo a seguir gera CS0059:  
  
```  
// CS0059.cs class MyClass //defaults to private accessibility // try the following line instead // public class MyClass { } public delegate void MyClassDel( MyClass myClass);   // CS0059 public class Program { public static void Main() { } }  
```