---
title: "CS0833 de erro do compilador | Microsoft Docs"
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
  - "CS0833"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0833"
ms.assetid: 4ae32454-265f-47aa-bf2a-ee1d702330b7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0833 de erro do compilador
Um tipo anônimo não pode ter várias propriedades com o mesmo nome.  
  
 Um tipo anônimo, assim como qualquer tipo, não é possível ter duas propriedades que têm o mesmo nome.  
  
### Para corrigir este erro  
  
1.  Dê um nome exclusivo de cada propriedade no tipo.  
  
## Exemplo  
 O exemplo a seguir gera CS0833:  
  
```  
// cs0833.cs using System; public class C { public static int Main() { var c = new { p1 = 1, p1 = 2 }; // CS0833 return 1; } }  
```  
  
## Consulte também  
 [Tipos anônimos](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)