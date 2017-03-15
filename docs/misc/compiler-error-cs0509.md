---
title: "CS0509 de erro do compilador | Microsoft Docs"
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
  - "CS0509"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0509"
ms.assetid: dc113e03-7a01-489b-b886-51ee056fc96a
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0509 de erro do compilador
'class1': não é possível derivar do tipo sealed 'class2'  
  
 Um [lacrado](/dotnet/csharp/language-reference/keywords/sealed) classe não pode atuar como um [base](/dotnet/csharp/language-reference/keywords/base) classe. Estruturas são seladas por padrão.  
  
 O exemplo a seguir gera CS0509:  
  
```  
// CS0509.cs // compile with: /target:library sealed public class clx {} public class cly : clx {}   // CS0509  
```