---
title: "CS0685 de erro do compilador | Microsoft Docs"
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
  - "CS0685"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0685"
ms.assetid: 20d7c6cf-a388-430f-b22b-232536912491
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0685 de erro do compilador
Membro Conditional 'member' não pode ter um parâmetro out  
  
 Ao usar o <xref:System.Diagnostics.ConditionalAttribute> atributo em um método que o método não pode ter um parâmetro de saída. Isso ocorre porque o valor da variável usado para o parâmetro de saída não seria definido no caso em que a chamada do método é compilada como nothing. Para evitar esse erro, remova o parâmetro fora da declaração do método condicional ou não use o atributo condicional.  
  
## Exemplo  
 O exemplo a seguir gera CS0685:  
  
```  
// CS0685.cs using System.Diagnostics; class C { [Conditional("DEBUG")] void trace(out int i)  // CS0685 { i = 1; } }  
```