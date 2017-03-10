---
title: "CS0720 de erro do compilador | Microsoft Docs"
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
  - "CS0720"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0720"
ms.assetid: 1a8e7613-6bfb-4178-a8b4-f4591316c0b8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0720 de erro do compilador
'classe estática': não é possível declarar indexadores em uma classe estática  
  
 Indexadores não são significativos em classes estáticas, uma vez que só podem ser usados com instâncias, e não é possível criar instâncias de um tipo estático.  
  
## Exemplo  
 O exemplo a seguir gera CS0720:  
  
```  
// CS0720.cs public static class Test { public int this[int index]  // CS0720 { get { return 1; } set {} } static void Main() {} }  
```