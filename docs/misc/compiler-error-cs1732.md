---
title: "CS1732 de erro do compilador | Microsoft Docs"
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
  - "CS1732"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1732"
ms.assetid: 72c7f7fc-d5f2-4538-9b02-50dda54d3b1e
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1732 de erro do compilador
Parâmetro esperado.  
  
 Esse erro é gerado quando uma expressão lambda contém uma vírgula após um parâmetro de entrada, mas não especificar o parâmetro a seguir.  
  
### Para corrigir este erro  
  
1.  Remova a vírgula, ou adicionar o parâmetro de entrada que o compilador espera encontrar após a vírgula.  
  
## Exemplo  
 O exemplo a seguir produz CS1732:  
  
```  
// cs1732.cs // compile with: /target:library class Test { delegate void D(int x, int y); static void Main() { D d = (x,) => { }; // CS1732 } }  
```