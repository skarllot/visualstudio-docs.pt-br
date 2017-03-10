---
title: "CS0623 de erro do compilador | Microsoft Docs"
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
  - "CS0623"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0623"
ms.assetid: c9fd6888-b9c5-48bf-b25b-2fae1446ad24
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0623 de erro do compilador
Inicializadores de matriz só podem ser usados em um inicializador de campo ou variável. Tente usar uma nova expressão.  
  
 Foi feita uma tentativa para inicializar uma matriz usando um inicializador de matriz em um contexto onde não é permitido.  
  
## Exemplo  
 O exemplo a seguir produz CS0623 porque o compilador interpreta o \\{4\\} como o inicializador de matriz incorporado dentro do inicializador de matriz externa:  
  
```  
//cs0632.cs using System; class X { public int[] x = { 2, 3, {4}}; //CS0623 }  
```  
  
## Consulte também  
 [Matrizes](/dotnet/csharp/programming-guide/arrays/index)