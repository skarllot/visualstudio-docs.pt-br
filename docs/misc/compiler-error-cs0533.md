---
title: "CS0533 de erro do compilador | Microsoft Docs"
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
  - "CS0533"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0533"
ms.assetid: f8b38c5a-d365-4081-a101-6282bdd19069
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0533 de erro do compilador
'membro de classe derivado' oculta o membro abstrato herdado 'membro da classe base'  
  
 Uma base de [classe](/dotnet/csharp/language-reference/keywords/class) método está oculto. Verifique a sintaxe da sua declaração para ver se ele está correto.  
  
 Para obter mais informações, consulte [base](/dotnet/csharp/language-reference/keywords/base).  
  
 O exemplo a seguir gera CS0533:  
  
```  
// CS0533.cs namespace x { abstract public class a { abstract public void f(); } abstract public class b : a { new abstract public void f();   // CS0533 // try the following lines instead // override public void f() // { // } public static void Main() { } } }  
```