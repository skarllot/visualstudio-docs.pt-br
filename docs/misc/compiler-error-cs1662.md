---
title: "CS1662 de erro do compilador | Microsoft Docs"
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
  - "CS1662"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1662"
ms.assetid: e61a4fc8-0ef1-4a4a-a27b-3a015c3ba38a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1662 de erro do compilador
Não é possível converter o bloco de método anônimo delegate tipo 'tipo de delegado' porque alguns dos tipos de retorno no bloco não são implicitamente conversíveis para o tipo de retorno do delegado  
  
 Esse erro ocorre se a instrução return do bloco de método anônimo tinha um tipo que não foi implicitamente conversível para o tipo de retorno do delegado.  
  
 O exemplo a seguir gera CS1662:  
  
```  
// CS1662.cs delegate int MyDelegate(int i); class C { public static void Main() { MyDelegate d = delegate(int i) { return 1.0; };  // CS1662 // Try this instead: // MyDelegate d = dekegate(int i) { return (int)1.0; }; } }  
```