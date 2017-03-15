---
title: "CS1728 de erro do compilador | Microsoft Docs"
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
  - "CS1728"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1728"
ms.assetid: 79a957db-ff56-4da6-9c17-8c5cffa1df5a
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1728 de erro do compilador
Não é possível associar delegado 'member' porque ele é um membro de 'type'  
  
 Não é possível associar delegados a membros de `Nullable` tipos.  
  
## Exemplo  
 O exemplo a seguir gera CS1728:  
  
```  
// CS1728.cs class Test { delegate T GetT<T>(); delegate T GetT1<T>(T t); delegate bool E(object o); delegate int I(); delegate string S(); static void Main() { int? x = null; int? y = 5; GetT<int> d1 = x.GetValueOrDefault;   // CS1728 GetT<int> d2 = y.GetValueOrDefault;   // CS1728 GetT1<int> d3 = x.GetValueOrDefault;   // CS1728 GetT1<int> d4 = y.GetValueOrDefault;   // CS1728 } }  
```