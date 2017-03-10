---
title: "CS0753 de erro do compilador | Microsoft Docs"
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
  - "CS0753"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0753"
ms.assetid: 287dd9da-da74-4290-9fa1-21ef1a8150fe
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0753 de erro do compilador
Somente métodos, classes, estruturas ou interfaces podem ser parciais.  
  
 O [parcial](/dotnet/csharp/language-reference/keywords/partial-type) modificador só pode ser usado com classes, estruturas, interfaces e métodos.  
  
### Para corrigir este erro  
  
1.  Remover o `partial` modificador da construção de variável ou idioma.  
  
## Exemplo  
 O código a seguir gera CS0753:  
  
```  
// cs0753.cs using System; public partial class C { partial int num; // CS0753 public static int Main() { return 1; } }  
```  
  
## Consulte também  
 [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)