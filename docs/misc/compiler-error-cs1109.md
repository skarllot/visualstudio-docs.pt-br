---
title: "CS1109 de erro do compilador | Microsoft Docs"
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
  - "CS1109"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1109"
ms.assetid: bebe56b8-3831-4ebb-a49e-e0364b4c11a7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1109 de erro do compilador
Métodos de extensão devem ser definidos em classes estáticas de nível superior, 'name' é uma classe aninhada.  
  
 Métodos de extensão não podem ser definidos em classes aninhadas.  
  
## Exemplo  
 O exemplo a seguir gera CS1109 porque a classe `Extension` é aninhada dentro da classe `Out`:  
  
```  
// cs1109.cs public class Test { } static class Out { static class Extension { static void ExtMethod(this Test c) // CS1109 { } } }  
```  
  
## Consulte também  
 [Métodos de extensão](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)