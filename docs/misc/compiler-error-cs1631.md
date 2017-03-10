---
title: "CS1631 de erro do compilador | Microsoft Docs"
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
  - "CS1631"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1631"
ms.assetid: bf0c5ff9-90a3-4db6-b4ee-0b93e31614e0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1631 de erro do compilador
Não é possível usar a instrução yield no corpo de uma cláusula catch  
  
 A instrução yield não é permitida de dentro do corpo de uma cláusula catch. Para evitar esse erro, mova a instrução yield fora do corpo de uma cláusula catch.  
  
 O exemplo a seguir gera CS1631:  
  
```  
// CS1631.cs using System; using System.Collections; public class C : IEnumerable { public IEnumerator GetEnumerator() { try { } catch(Exception e) { yield return this;  // CS1631 } } public static void Main() { } }  
```