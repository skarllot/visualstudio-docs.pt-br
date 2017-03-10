---
title: "CS1676 de erro do compilador | Microsoft Docs"
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
  - "CS1676"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1676"
ms.assetid: 5ac83d98-5baa-49fd-b76a-d8ef0865b9dd
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1676 de erro do compilador
O parâmetro 'number' deve ser declarado com a palavra\-chave 'palavra\-chave'  
  
 Esse erro ocorre quando o modificador de parâmetro de tipo em um método anônimo é diferente daquele usado na declaração do delegado que está convertendo o método.  
  
 O exemplo a seguir gera CS1676:  
  
```  
// CS1676.cs delegate void E(ref int i); class Errors { static void Main() { E e = delegate(out int i) { };   // CS1676 // To resolve, use the following line instead: // E e = delegate(ref int i) { }; } }  
```