---
title: "CS0687 de erro do compilador | Microsoft Docs"
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
  - "CS0687"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0687"
ms.assetid: b51c5e7c-f4de-4aa4-97b1-ebe220cd19b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0687 de erro do compilador
O qualificador alias de namespace ':: ' sempre resolve para um tipo ou namespace por isso é inválido aqui. Considere o uso de '.' em vez disso.  
  
 Esse erro ocorre se você tiver usado algo que o analisador é interpretado como um tipo em um lugar inesperado. Um nome de namespace ou tipo é válido somente em uma expressão de acesso de membro, usando o acesso do membro \(**.**\) operador. Isso pode ocorrer se você usou o operador de escopo global \(:\) em outro contexto.  
  
## Exemplo  
 O exemplo a seguir gera CS0687:  
  
```  
// CS0687.cs using M = Test; using System; public class Test { public static int x = 77; public static void Main() { Console.WriteLine(M::x); // CS0687 // To resolve use the following line instead: // Console.WriteLine(M.x); } }  
```