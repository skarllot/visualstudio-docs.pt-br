---
title: "CS0185 de erro do compilador | Microsoft Docs"
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
  - "CS0185"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0185"
ms.assetid: d6546e10-0af3-4860-8e6f-2da7dbeb3d28
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0185 de erro do compilador
'type' não é um tipo de referência necessária à instrução lock  
  
 O [bloqueio](/dotnet/csharp/language-reference/keywords/lock-statement) instrução só pode avaliar os tipos de referência. Para obter mais informações, consulte [Sincronização de thread](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md) e [Tipos de referência](/dotnet/csharp/language-reference/keywords/reference-types).  
  
## Exemplo  
 O exemplo a seguir gera CS0185:  
  
```  
// CS0185.cs public class MainClass { public static void Main () { lock (1)   // CS0185 // try the following lines instead // MainClass x = new MainClass(); // lock(x) { } } }  
```