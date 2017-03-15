---
title: "CS0119 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0119"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0119"
ms.assetid: 048924f1-378f-4021-bd20-299d3218f810
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0119 de erro do compilador
'construct1\_name' é 'construct1', que não é válido no contexto especificado.  
  
 O compilador detectou uma construção inesperada, como o seguinte:  
  
-   Um construtor de classe não é uma expressão de teste válidos em uma instrução condicional.  
  
-   Um nome de classe foi usado em vez de um nome de instância para se referir a um elemento de matriz.  
  
-   Um identificador de método é usado como se fosse uma classe ou struct  
  
## Exemplo  
 O exemplo a seguir gera CS0119.  
  
```  
// CS0119.cs using System; public class MyClass { public static void Test() {} public static void Main() { Console.WriteLine(Test.x);   // CS0119 } }  
```