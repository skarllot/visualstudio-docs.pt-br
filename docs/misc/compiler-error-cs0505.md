---
title: "CS0505 de erro do compilador | Microsoft Docs"
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
  - "CS0505"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0505"
ms.assetid: e3cb9e33-7338-4869-859b-81d7439f0d23
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0505 de erro do compilador
'member1': não é possível substituir porque 'member2' não é uma função  
  
 Uma declaração de classe tentou substituir um método\-não na classe base. Substituições devem corresponder ao tipo de membro. Se um método com o mesmo nome como um método em uma classe base for desejado, use [novo](/dotnet/csharp/language-reference/keywords/new) \(e não [substituir](/dotnet/csharp/language-reference/keywords/override)\) na declaração do método na classe base.  
  
 O exemplo a seguir gera CS0505:  
  
```  
// CS0505.cs // compile with: /target:library public class clx { public int i; } public class cly : clx { public override int i() { return 0; }   // CS0505 }  
```