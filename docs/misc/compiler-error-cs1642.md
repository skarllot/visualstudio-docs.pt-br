---
title: "CS1642 de erro do compilador | Microsoft Docs"
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
  - "CS1642"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1642"
ms.assetid: 2efeedf1-1839-485d-8b8c-9045df1951f0
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1642 de erro do compilador
Campos de buffer de tamanho fixo só podem ser membros de estruturas.  
  
 Esse erro ocorre se você usar um campo de buffer de tamanho fixo em um `class`, em vez de um `struct`. Para resolver esse erro, altere o `class` para um `struct` ou declarar o campo como uma matriz comum.  
  
## Exemplo  
 O exemplo a seguir gera CS1642.  
  
```  
// CS1642.cs // compile with: /unsafe /target:library unsafe class C { fixed int a[10];   // CS1642 } unsafe struct D { fixed int a[10]; } unsafe class E { public int[] a = null; }  
```