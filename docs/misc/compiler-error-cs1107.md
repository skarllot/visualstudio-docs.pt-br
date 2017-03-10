---
title: "CS1107 de erro do compilador | Microsoft Docs"
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
  - "CS1107"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1107"
ms.assetid: 1b6f6790-53af-4261-a14f-bf2db9790f0b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1107 de erro do compilador
Um parâmetro só pode ter um modificador 'nome do modificador'.  
  
 É um erro de modificadores de parâmetro, como `this`, `ref`, e `out` aparecer mais de uma vez em uma definição de parâmetro.  
  
## Exemplo  
 O exemplo a seguir gera CS1107:  
  
```  
// cs1107.cs public static class Test { // Extension methods. public static void TestMethod(this this t) {} // CS1107 // Regular Instance Method public void TestMethod(ref ref int i) {} // CS1107 }  
```