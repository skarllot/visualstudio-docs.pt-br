---
title: "CS1014 de erro do compilador | Microsoft Docs"
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
  - "CS1014"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1014"
ms.assetid: 60c1e9af-5a0d-4ae0-a2e6-881b0d1535e9
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1014 de erro do compilador
Um acessador get ou set esperado  
  
 Uma declaração de método foi encontrada em uma declaração de propriedade. Você só pode declarar `get` e `set` métodos em uma propriedade.  
  
 Para obter mais informações sobre propriedades, consulte [Usando propriedades](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Exemplo  
 O exemplo a seguir gera CS1014.  
  
```  
// CS1014.cs // compile with: /target:library class Sample { public int TestProperty { get { return 0; } int z;   // CS1014  not get or set } }  
```