---
title: "CS0442 de erro do compilador | Microsoft Docs"
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
  - "CS0442"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0442"
ms.assetid: a411660d-0db6-4b63-b19e-f4538fc201e5
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0442 de erro do compilador
'Property': propriedades abstratas não podem ter acessadores particulares  
  
 Esse erro ocorre quando você usar o modificador de acesso "privado" para modificar um acessador abstrato. Para resolver, use um modificador de acesso diferente ou tornar a propriedade não\-abstrata.  
  
## Exemplo  
 O exemplo a seguir gera CS0442:  
  
```  
// CS0442.cs public abstract class MyClass { public abstract int AbstractProperty { get; private set;   // CS0442 // Try this instead: // set; } }  
```