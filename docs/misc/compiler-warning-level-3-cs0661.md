---
title: "Compilador CS0661 de aviso (n&#237;vel 3) | Microsoft Docs"
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
  - "CS0661"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0661"
ms.assetid: c218665e-5947-40bb-b633-d268483e6522
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0661 de aviso (n&#237;vel 3)
'class' define o operador \= \= ou operador\! \= mas não substitui Object.GetHashCode\(\)  
  
 O compilador detectou a igualdade definido pelo usuário ou operador de desigualdade, mas nenhuma substituição para o **GetHashCode** função. Um operador de igualdade ou desigualdade definido pelo usuário implica que você também queira substituir o **GetHashCode** função.  
  
 O exemplo a seguir gera CS0661:  
  
```  
// CS0661.cs // compile with: /W:3 class Test   // CS0661 { public static bool operator == (object o, Test t) { return true; } public static bool operator != (object o, Test t) { return true; } public override bool Equals(object o) { return true; } // uncomment the GetHashCode function to resolve // public override int GetHashCode() // { //    return 0; // } public static void Main() { } }  
```