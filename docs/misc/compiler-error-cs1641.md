---
title: "CS1641 de erro do compilador | Microsoft Docs"
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
  - "CS1641"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1641"
ms.assetid: ba6eab47-c28b-4531-b6a0-6d538b236d19
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1641 de erro do compilador
Um campo de buffer de tamanho fixo deve ter especificador de tamanho de matriz após o nome do campo  
  
 Ao contrário de matrizes regulares, buffers de tamanho fixo exigem um tamanho constante a ser especificado no ponto de declaração. Para resolver esse erro, adicione uma literal de inteiro positivo ou um constante inteiro positivo e coloque colchetes após o identificador.  
  
 O exemplo a seguir gera CS1641:  
  
```  
// CS1641.cs // compile with: /unsafe /target:library unsafe struct S { fixed int [] a;  // CS1641 // OK fixed int b [10]; const int c = 10; fixed int d [c]; }  
```