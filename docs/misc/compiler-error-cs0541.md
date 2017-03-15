---
title: "CS0541 de erro do compilador | Microsoft Docs"
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
  - "CS0541"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0541"
ms.assetid: ed812c07-24f7-43c6-9a44-553f27f6249d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0541 de erro do compilador
'declaração de ': declaração de interface explícita só pode ser declarada em uma classe ou struct  
  
 Explícito [interface](/dotnet/csharp/language-reference/keywords/interface) declaração foi encontrada fora de um [classe](/dotnet/csharp/language-reference/keywords/class) ou [struct](/dotnet/csharp/language-reference/keywords/struct).  
  
 O exemplo a seguir gera CS0541:  
  
```  
// CS0541.cs namespace x { interface IFace { void F(); } interface IFace2 : IFace { void IFace.F();   // CS0541 } }  
```