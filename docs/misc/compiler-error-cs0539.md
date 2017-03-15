---
title: "CS0539 de erro do compilador | Microsoft Docs"
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
  - "CS0539"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0539"
ms.assetid: 41b8975c-abd1-4a36-98a4-8efa5fb0502a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0539 de erro do compilador
membro na declaração de interface explícita não é um membro de interface  
  
 Foi feita uma tentativa para declarar explicitamente uma [interface](/dotnet/csharp/language-reference/keywords/interface) membro que não existe. Você deve excluir a declaração ou alterá\-lo para que ele se refere a um membro de interface válido.  
  
 O exemplo a seguir gera CS0539:  
  
```  
// CS0539.cs namespace x { interface I { void m(); } public class clx : I { void I.x()   // CS0539 { } public static int Main() { return 0; } } }  
```