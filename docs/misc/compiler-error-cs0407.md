---
title: "CS0407 de erro do compilador | Microsoft Docs"
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
  - "CS0407"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0407"
ms.assetid: 59112fb9-4641-466e-b738-b3228539a09e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0407 de erro do compilador
'tipo de retorno de método' tem o tipo de retorno incorreto  
  
 O método não era compatível com o tipo de delegado. Os tipos de argumento corresponderam, mas o tipo de retorno não era do tipo de retorno correto para esse delegado. Para evitar esse erro, use um método diferente, altere o tipo de retorno do método ou alterar tipo de retorno do delegado.  
  
## Exemplo  
 O exemplo a seguir gera CS0407:  
  
```  
// CS0407.cs public delegate int MyDelegate(); class C { MyDelegate d; public C() { d = new MyDelegate(F);  // OK: F returns int d = new MyDelegate(G);  // CS0407 – G doesn't return int } public int F() { return 1; } public void G() { } public static void Main() { C c1 = new C(); } }  
```