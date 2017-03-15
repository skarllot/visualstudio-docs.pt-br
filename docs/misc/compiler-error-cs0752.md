---
title: "CS0752 de erro do compilador | Microsoft Docs"
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
  - "CS0752"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0752"
ms.assetid: f9a373d6-31ed-42db-8206-80cbe9b8c546
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0752 de erro do compilador
Um método parcial não pode ter parâmetros out  
  
 Um método parcial não pode ter um [out](/dotnet/csharp/language-reference/keywords/out) parâmetro. Parâmetros de saída não são permitidas porque se o método parcial é removido pelo compilador, não há nenhuma garantia de que o parâmetro de saída é atribuído.  
  
### Para corrigir este erro  
  
1.  Remova o modificador fora do parâmetro e use o valor de retorno do método, ou então remova o modificador parcial da declaração de método.  
  
## Exemplo  
 O código a seguir gera CS0752:  
  
```  
// cs0752.cs public partial class C { partial void Part(out int num); // CS0752 // try the following line instead // partial void Part(int num); public static int Main() { return 1; } }  
```  
  
## Consulte também  
 [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)