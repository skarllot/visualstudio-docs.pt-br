---
title: "CS0406 de erro do compilador | Microsoft Docs"
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
  - "CS0406"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0406"
ms.assetid: 9d69681c-e261-4e5e-9361-ea566de12f2e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0406 de erro do compilador
A restrição de tipo de classe 'restrição' deve vir antes de qualquer outra restrição  
  
 Quando um tipo genérico ou método tem uma restrição de tipo de classe, essa restrição deve ser listada primeiro. Para evitar esse erro, mova a restrição de tipo de classe para o início da lista de restrições.  
  
## Exemplo  
 O exemplo a seguir gera CS0406.  
  
```  
// CS0406.cs // compile with: /target:library interface I {} class C {} class D<T> where T : I, C {}   // CS0406 class D2<T> where T : C, I {}   // OK  
```