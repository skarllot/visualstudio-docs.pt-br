---
title: "CS0758 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0758"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0758"
ms.assetid: 06ddd548-1311-40db-9078-8a18107b8346
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0758 de erro do compilador
As duas declarações de métodos parciais devem usar um parâmetro params ou nenhuma delas deve usar um parâmetro params  
  
 Se uma parte de um método parcial especifica um `params` parâmetro, a outra parte deve especificar um também.  
  
### Para corrigir este erro  
  
1.  Adicione o `params` modificador em uma parte do método, ou removê\-lo em outro.  
  
## Exemplo  
 O código a seguir gera CS0758:  
  
```  
using System; public partial class C { partial void Part(int i, params char[] array); partial void Part(int i, char[] array) // CS0758 { } public static int Main() { return 1; } }  
```  
  
## Consulte também  
 [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [params](/dotnet/csharp/language-reference/keywords/params)