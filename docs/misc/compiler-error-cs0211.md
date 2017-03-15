---
title: "CS0211 de erro do compilador | Microsoft Docs"
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
  - "CS0211"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0211"
ms.assetid: 720be9a9-b0c1-4391-94e5-4c4027e83036
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0211 de erro do compilador
Não é possível obter o endereço da expressão especificada  
  
 Você pode obter o endereço de campos, variáveis locais e indireção de ponteiros, mas você não pode obter, por exemplo, o endereço da soma das duas variáveis locais. Para obter mais informações, consulte [Código não seguro e ponteiros](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
 O exemplo a seguir gera CS0211:  
  
```  
// CS0211.cs // compile with: /unsafe public class MyClass { unsafe public void M() { int a = 0, b = 0; int *i = &(a + b);   // CS0211, the addition of two local variables // try the following line instead // int *i = &a; } public static void Main() { } }  
```