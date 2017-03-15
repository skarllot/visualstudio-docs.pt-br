---
title: "CS1609 de erro do compilador | Microsoft Docs"
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
  - "CS1609"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1609"
ms.assetid: 89e112f8-6337-4803-8741-2e38497deb8c
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1609 de erro do compilador
Modificadores não podem ser colocados em declarações de acessador de evento  
  
 Modificadores só podem ser colocados em declarações de evento e não em declarações de acessador de evento. Para obter mais informações, consulte [Usando propriedades](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Exemplo  
 O exemplo a seguir gera CS1609.  
  
```  
// CS1609.cs // compile with: /target:library delegate int Del(); class A { public event Del MyEvent { private add {}   // CS1609 // try the following line instead // add {} remove {} } }  
```