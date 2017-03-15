---
title: "CS0139 de erro do compilador | Microsoft Docs"
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
  - "CS0139"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0139"
ms.assetid: 235ba3d4-566c-4ef6-801a-a338f4f2a12d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0139 de erro do compilador
Nenhum loop delimitador a partir do qual quebrar ou continuar  
  
 A interromper ou continuar a instrução foi encontrada fora de um loop.  
  
 Para obter mais informações, consulte [saltar instruções](/dotnet/csharp/language-reference/keywords/jump-statements).  
  
 O exemplo a seguir gera CS0139 duas vezes:  
  
```  
// CS0139.cs namespace x { public class a { public static void Main() { continue;  // CS0139 break;     // CS0139 } } }  
```