---
title: "Compilador CS0437 de aviso (n&#237;vel 2) | Microsoft Docs"
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
  - "CS0437"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0437"
ms.assetid: cba5c9b6-a0bc-4f19-b1f0-c1f66436ee91
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0437 de aviso (n&#237;vel 2)
O tipo 'type' em 'assembly2' está em conflito com o namespace importado 'namespace' em 'fassembly1'. Usando o tipo definido no 'assembly'.  
  
 Esse aviso é emitido quando um tipo em um arquivo de origem, file\_2, entra em conflito com um namespace importado no 1 do arquivo. O compilador usa o tipo de arquivo de origem.  
  
## Exemplo  
  
```  
// CS0437_a.cs // compile with: /target:library namespace Util { public class A { public void Test() { System.Console.WriteLine("CS0437_a.cs"); } } }  
```  
  
## Exemplo  
 O exemplo a seguir gera CS0437.  
  
```  
// CS0437_b.cs // compile with: /reference:CS0437_a.dll /W:2 // CS0437 expected class Util { public class A { public void Test() { System.Console.WriteLine("CS0437_b.cs"); } } } public class Test { public static void Main() { Util.A x = new Util.A(); x.Test(); } }  
```