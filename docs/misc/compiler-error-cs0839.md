---
title: "CS0839 de erro do compilador | Microsoft Docs"
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
  - "CS0839"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0839"
ms.assetid: 6f2f1062-8551-4125-8880-68bfbfbcf061
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0839 de erro do compilador
Argumento ausente.  
  
 Um argumento está ausente na chamada do método.  
  
### Para corrigir este erro  
  
1.  Verificar a assinatura do método Double e localize e fornecer o argumento ausente.  
  
## Exemplo  
 O exemplo a seguir gera CS0839:  
  
```  
// cs0839.cs using System; namespace TestNamespace { class Test { static int Add(int i, int j) { return i + j; } static int Main() { int i = Test.Add( , 5); // CS0839 return 1; } } }  
```