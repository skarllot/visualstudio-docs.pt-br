---
title: "CS1663 de erro do compilador | Microsoft Docs"
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
  - "CS1663"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1663"
ms.assetid: 013f36ac-8925-4cee-9008-54fa7ad1324b
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1663 de erro do compilador
Tipo de buffer de tamanho fixo deve ser um dos seguintes: bool, byte, short, int, long, char, sbyte, ushort, uint, ulong, float ou double  
  
 Um buffer de tamanho fixo não pode ser qualquer tipo, exceto os listados. Para evitar esse erro, use outro tipo ou não use uma matriz fixa.  
  
## Exemplo  
 O exemplo a seguir gera CS1663.  
  
```  
// CS1663.cs // compile with: /unsafe /target:library unsafe struct C { fixed string ab[10];   // CS1663 }  
```