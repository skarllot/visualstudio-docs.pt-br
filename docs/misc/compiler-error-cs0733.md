---
title: "CS0733 de erro do compilador | Microsoft Docs"
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
  - "CS0733"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0733"
ms.assetid: 1b0150e0-48d3-4b9c-85cc-27346e4f5f84
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0733 de erro do compilador
Não é possível encaminhar tipo genérico, 'GenericType \<\>'  
  
## Exemplo  
 O exemplo a seguir gera CS0733. Compile o arquivo primeiro como uma biblioteca e, em seguida, fazer referência a ela quando você compila o segundo arquivo.  
  
```  
// CS0733a.cs // compile with: /target:library public class GenericType<T> { }  
```  
  
```  
// CS0733.cs // compile with: /target:library /r:CS0733a.dll [assembly: System.Runtime.CompilerServices.TypeForwardedTo(typeof(GenericType<int>))]   // CS0733  
```