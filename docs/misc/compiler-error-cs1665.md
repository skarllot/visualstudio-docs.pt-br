---
title: "CS1665 de erro do compilador | Microsoft Docs"
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
  - "CS1665"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1665"
ms.assetid: 93d4a4af-23c3-4730-a778-77852e41db4d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1665 de erro do compilador
Buffers de tamanho fixo devem ter um comprimento maior que zero  
  
 Esse erro ocorre se um buffer de tamanho fixo é declarado com um zero ou negativo de tamanho. O comprimento do buffer de tamanho fixo deve ser um inteiro positivo.  
  
## Exemplo  
 O exemplo a seguir gera CS1665.  
  
```  
// CS1665.cs // compile with: /unsafe /target:library struct S { public unsafe fixed int A[0];   // CS1665 }  
```