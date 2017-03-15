---
title: "CS0528 de erro do compilador | Microsoft Docs"
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
  - "CS0528"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0528"
ms.assetid: 8f5dde55-7e4f-4ffa-be14-0e0f3a538118
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0528 de erro do compilador
'interface' já está listado na lista de interface  
  
 Uma lista de herança da interface inclui uma duplicata. Um [interface](/dotnet/csharp/language-reference/keywords/interface) só pode ser especificada uma vez na lista de herança.  
  
 O exemplo a seguir gera CS0528:  
  
```  
// CS0528.cs namespace x { public interface a { } public class b : a, a   // CS0528 { public void Main() { } } }  
```