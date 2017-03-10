---
title: "CS0763 de erro do compilador | Microsoft Docs"
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
  - "CS0763"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0763"
ms.assetid: 940870ba-1250-4365-acaa-7f968ee96c5b
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0763 de erro do compilador
As duas declarações de métodos parciais devem ser estáticas ou nenhuma delas deve ser estática.  
  
 Uma declaração de método parcial não pode ter uma parte estática e a outra parte não estática.  
  
### Para corrigir este erro  
  
1.  Verifique as duas partes estáticas ou não estático.  
  
## Exemplo  
 O código a seguir gera CS0763:  
  
```  
// cs0763.cs using System; public partial class C { static partial void Part(); partial void Part() // CS0763 { } public static int Main() { return 1; } }  
```  
  
## Consulte também  
 [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [static](/dotnet/csharp/language-reference/keywords/static)