---
title: "CS0751 de erro do compilador | Microsoft Docs"
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
  - "CS0751"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0751"
ms.assetid: 2ebaed5f-d3ca-452f-8fce-f3299b84360a
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0751 de erro do compilador
Um método parcial deve ser declarado em uma classe ou struct parcial  
  
 Não é possível declarar um [parcial](/dotnet/csharp/language-reference/keywords/partial-method) método, a menos que ela é encapsulada em uma classe parcial ou estrutura parcial.  
  
### Para corrigir este erro  
  
1.  Remova o `partial` modificador do método e fornecer uma implementação, ou então adicionar o `partial` modificador para a classe ou struct delimitador.  
  
## Exemplo  
 O exemplo a seguir gera CS0751:  
  
```  
// cs0751.cs using System; public class C { partial void Part(); // CS0751 public static int Main() { return 1; } }  
```  
  
## Consulte também  
 [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)