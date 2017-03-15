---
title: "CS0748 de erro do compilador | Microsoft Docs"
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
  - "CS0748"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0748"
ms.assetid: da1935af-a5ea-41f4-84ae-58559b750566
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0748 de erro do compilador
Uso do parâmetro lambda inconsistente; todos os tipos de parâmetro devem ser explícita ou implícita.  
  
 Se uma expressão lambda tem vários parâmetros de entrada, alguns parâmetros não podem usar digitação implícita enquanto outros usam uma digitação explícita.  
  
### Para corrigir este erro  
  
1.  Dar a todos os parâmetros de entrada tipos implícitos ou fornecer todos os tipos explícitos.  
  
## Exemplo  
 O código a seguir gera CS0748 porque, na expressão lambda, apenas `alpha` tem um tipo explícito:  
  
```  
// cs0748.cs class CS0748 { delegate double D(int x, int y); D d = (int alpha, beta) => { return beta / alpha; }; // CS0748 }  
```  
  
## Consulte também  
 [Expressões lambda](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions)