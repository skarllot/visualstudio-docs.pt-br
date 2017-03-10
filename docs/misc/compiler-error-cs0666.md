---
title: "CS0666 de erro do compilador | Microsoft Docs"
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
  - "CS0666"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0666"
ms.assetid: 44ad4574-b4a2-487b-8d05-0116762231ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0666 de erro do compilador
'member': novo membro protegido declarado em struct  
  
 Um [struct](/dotnet/csharp/language-reference/keywords/struct) não pode ser [abstrato](/dotnet/csharp/language-reference/keywords/abstract) e é sempre implicitamente [lacrado](/dotnet/csharp/language-reference/keywords/sealed). Como estruturas não oferecem suporte a herança, o conceito de um [protegido](/dotnet/csharp/language-reference/keywords/protected) membro em um struct não faz sentido. Para obter mais informações, consulte [Herança](/dotnet/csharp/programming-guide/classes-and-structs/inheritance).  
  
## Exemplo  
 O exemplo a seguir gera CS0666:  
  
```  
// CS0666.cs class M { static void Main() { } } struct S { protected int x;   // CS0666 }  
```