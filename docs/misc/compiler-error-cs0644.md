---
title: "CS0644 de erro do compilador | Microsoft Docs"
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
  - "CS0644"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0644"
ms.assetid: 835f3ee2-f897-4ba2-ad13-af629a9ab7fe
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0644 de erro do compilador
'class1' não pode derivar de classe especial 'class2'  
  
 Classes explicitamente não podem herdar de qualquer uma das seguintes classes base:  
  
-   **System. Enum**  
  
-   **ValueType**  
  
-   **Delegate**  
  
-   **Array**  
  
 Eles são usados como classes base implícitas pelo compilador. Por exemplo, **ValueType** é a classe de base implícita de estruturas.  
  
 O exemplo a seguir gera CS0644:  
  
```  
// CS0644.cs class MyClass : System.ValueType   // CS0644 { }  
```