---
title: "CS1948 de erro do compilador | Microsoft Docs"
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
  - "CS1948"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1948"
ms.assetid: 3dac3abe-0edd-4ee1-8fb1-bc597ea63e1f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1948 de erro do compilador
A variável de intervalo 'name' não pode ter o mesmo nome que um parâmetro de tipo de método  
  
 O mesmo espaço de declaração não pode conter duas declarações do mesmo identificador.  
  
### Para corrigir este erro  
  
1.  Altere o nome da variável de intervalo ou o parâmetro de tipo.  
  
## Exemplo  
 O exemplo a seguir gera CS1948 porque o identificador `T` é usado para a variável de intervalo e o parâmetro de tipo no método `TestMethod`:  
  
```  
// cs1948.cs using System.Linq; class Test { public void TestMethod<T>(T t) { var x = from T in Enumerable.Range(1, 100) // CS1948 select T; } }  
```